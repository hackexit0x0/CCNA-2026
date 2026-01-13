### Static Routing
> • It is configured by Administrator manually.\
> • Mandatory need of Destination Network ID\
> • It is Secure & fast\
> • Used for Small organizations with a network of 10-15 Routers\
> • Administrative distance for Static Route is 0 and 1.

>  **Administrative distance:**
It is the “trustworthiness” of the routing information. Lesser the Administrative distance,
higher the preference.

**Advantages:-**

> ✅ Simple and easy to configure\
> ✅ Best for small networks\
> ✅ No routing protocol overhead\
> ✅ Uses less CPU and memory\
> ✅ More secure (routes are not advertised)\
> ✅ Full administrator control over routing paths\
> ✅ Predictable and stable routing behavior

**Disadvantages:-**

> ❌ Suitable only for small networks\
> ❌ Manual configuration required on every router\
> ❌ No automatic route updates\
> ❌ Network changes affect the entire network\
> ❌ No failover unless manually configured\
> ❌ Not scalable for large or dynamic networks\
> ❌ Higher administrative effort

#### Configuring Static Route Comamnd
```py
Router(config)# ip route <Destination Network ID> <Destination Subnet Mask> <Next-hop IP address >
Or
Router(config)# ip route <Destination Network ID> <Destination Subnet Mask> <Exit interface type><interface number>
```
---
<img src="img-lab/1.png">


### R1 ON HYD :
```py
HYD # config terminal
HYD(config) # ip routing
HYD(config) # ip route 20.0.0.0 255.255.255.0 1.1.1.2
HYD # show ip route

C 10.0.0.0/8 is directly connected on Ethernet 0
C 1.0.0.0/8 is directly connected on serial 0
S 20.0.0.0/8 via [1/0] 1.1.1.2 
```

### R2 ON KSA :
```py
KSA # config terminal
KSA(config) # ip routing
KSA(config) # ip route 10.0.0.0 255.255.255.0 1.1.1.1
KSA # show ip route
C 20.0.0.0/8 is directly connected on Ethernet 0
C 1.0.0.0/8 is directly connected on serial 1
S 10.0.0.0/8 via [1/0] 1.1.1.1 
```