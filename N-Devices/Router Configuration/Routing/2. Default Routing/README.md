### Default Routes
> • Manually adding the single route for the entire destination. Default route is used when
destination is unknown\
> • Last preferred route in the routing table\
> • When there is no entry for the destination network in a routing table, the router will forward the packet to its default router.\
> • Default routes help in reducing the size of your routing table


### Configuring Default Route
```py
Router(config)# ip route <Destination Network ID> <Destination Subnet Mask>
 <Next-hop IP address >
 ```
> OR
```py
Router(config)# ip route <Destination Network ID> <Destination Subnet Mask>
 <Exit interface type><interface number>
```

<img src="img/1.png">

#### DEFAULT ROUTING:
#### [R1] ON HYD give default route.
```py
HYD # config terminal
HYD(config) # ip routing
HYD(config) # ip route 0.0.0.0 0.0.0.0 s0
HYD # show ip route

C 10.0.0.0/8 is directly connected on Ethernet 0
C 1.0.0.0/8 is directly connected on serial 0
S* 0.0.0.0 is directly connected on serial 0
```

#### [R2] ON KSA give static route.
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
#### [R3] ON DUBAI give default route.
```py
DUBAI # config terminal
DUBAI(config) # ip routing
DUBAI(config) # ip route 0.0.0.0 0.0.0.0 2.2.2.1
DUBAI # show ip route

C 30.0.0.0/8 is directly connected on Ethernet 0
C 2.0.0.0/8 is directly connected on serial 1
S* 20.0.0.0/8 via [1/0] 2.2.2.1
```