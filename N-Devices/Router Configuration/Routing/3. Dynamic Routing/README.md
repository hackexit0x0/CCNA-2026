### DYNAMIC ROUTING
> Advantages of Dynamic over static:> 
>There is no need to know the destination networks.\
>Need to advertise the directly connected networks.\
>Updates the topology changes dynamically.\
>Administrative work is reduced\
>Used for large organizations.\
>Neighbor routers exchange routing information and build the routing table
automatically.

> Types of Dynamic Routing Protocols> 
>Distance Vector Protocol\
>Link State Protocol\
>Hybrid Protocol\

---
| **Distance Vector Protocol** | **Link State Protocol** | **Hybrid Protocol** |
|-----------------------------|------------------------|---------------------|
| Works with Bellman-Ford algorithm | Works with Dijkstra algorithm | Also called Advanced Distance Vector Protocol |
| Periodic updates | Link-state updates | Works with DUAL algorithm |
| Classful routing protocol | Classless routing protocol | Link-state updates |
| Full routing tables are exchanged | Missing routes are exchanged | Classless routing protocol |
| Updates are through broadcast | Updates are through multicast | Missing routes are exchanged |
| Examples: RIP v1, RIP v2, IGRP | Examples: OSPF, IS-IS | Updates are through multicast |
| — | — | Example: EIGRP |
---

>  Administrative Distance
```py
• Rating of the Trustworthiness of a routing information source.
• The Number is between 0 and 255
• The higher the value, the lower the trust.
• Default administrative distances are as follows :
       • Directly Connected = 0
       • Static Route = 1
       • IGRP = 100
       • OSPF = 110
       • RIP = 120
       • EIGRP = 90/170
```