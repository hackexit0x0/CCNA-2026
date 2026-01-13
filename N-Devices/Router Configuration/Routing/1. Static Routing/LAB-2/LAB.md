### LAB 

<img src="2.png">

> SITE R1 ON HYD :
```py
HYD # config terminal
HYD(config) # ip routing
HYD(config) # ip route 20.0.0.0 255.0.0.0 1.1.1.2
HYD(config) # ip route 30.0.0.0 255.0.0.0 1.1.1.2
HYD(config) # ip route 2.0.0.0 255.0.0.0 1.1.1.2

HYD # show ip route

C 10.0.0.0/8 is directly connected on Ethernet 0
C 1.0.0.0/8 is directly connected on serial 0
S 20.0.0.0/8 via [1/0] 1.1.1.2
S 30.0.0.0/8 via [1/0] 1.1.1.2
S 2.0.0.0/8 via [1/0] 1.1.1.2

```
> SIET R2 ON KSA:
```py
KSA # config terminal
KSA(config) # ip routing
KSA(config) # ip route 10.0.0.0 255.0.0.0 1.1.1.1
KSA(config) # ip route 30.0.0.0 255.0.0.0 2.2.2.2

KSA # show ip route
C 20.0.0.0/8 is directly connected on Ethernet 0
C 1.0.0.0/8 is directly connected on serial 1
C 2.0.0.0/8 is directly connected on serial 0
S 30.0.0.0/8 via [1/0] 2.2.2.2
S 10.0.0.0/8 via [1/0] 1.1.1.1
```
> SIET R3 ON KSA:
```py
KSA # config terminal
KSA(config) # ip routing
KSA(config) # ip route 10.0.0.0 255.0.0.0 1.1.1.1
KSA(config) # ip route 30.0.0.0 255.0.0.0 2.2.2.2

KSA # show ip route
C 20.0.0.0/8 is directly connected on Ethernet 0
C 1.0.0.0/8 is directly connected on serial 1
C 2.0.0.0/8 is directly connected on serial 0
S 30.0.0.0/8 via [1/0] 2.2.2.2
S 10.0.0.0/8 via [1/0] 1.1.1.1
```