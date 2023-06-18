Let's compare 4D architecture to conventional IP routers.
 In Conventional IP routers, we can think of network management in terms of 3 planes.
1. management plane: constructs a network-wide view & can configure the routers
2. control plane: the control plane in 4D network is different from what we know. It's about routing protocols, track topology changes, compute routes & install forwarding tables, but isn't really about network-wide view.
3. data plane

 A goal in 4D is to remove conventional control plane (routing plane) like RCP paper, removing the functions of routing from routers. It includes faster innovation (remove dependence of vendors), simpler management system, easier interoperability between vendors (compatibility only in wire protocols), simpler and cheaper routers (little or no software on a router). The 4D architecture inspired OpenFlow movement, because it realized that it's actually possible to remove the control plane from routers. 
1. control software can run elsewhere 
2. state & computation is reasonable 
3. system overhead can be amortized, because a lot of functions are duplicated among routers
4. control plane can easily access to other info
5. some control can move to end hosts

The 4D architecture has 3 goals:
1. network-level objectives rather than router-level objectives
	- configure networks, not routers
	- minimize the maximum link utilization
	- connectivity under all layer-two failures
2. network-wide views
	- to drive decision-makings
	- traffic matrix, network topology, equipment
3. direct control
	- direct, sole control over data-plane config
	- packet forwarding, filtering, marketing, buffering, etc.

---

### The 4D Planes

1. **Decision**: all management & control, brain of the network, functions operating on view of entire network e.g. path selection & traffic engineering, reachability control & VPNs.
2. **Dissemination**: control channel, for decision & data plane communication, it's like BGP in RCP. Functions that support creation of a network-wide view e.g. topology discovery & other measurements, install state in data plane.
3. **Discovery**: allows decision plane to discover topology, monitor traffic, etc.
4. **Data**: forward traffic according to what is in the forwarding tables

> Abstractions should reduce complexity

Routing protocols carry a lot of data & complexity, but in 4D protocols are control channels.
- Application: traffic engineering (isolation) in 4D. Because the decision plane sees both traffic engineering and access control it can perform decisions that optimize traffic load while still respecting reachability constraints

---

### SDN & 4D
- control plane in 4D is actually distributed routing protocols
- what we refer to as control plane today is the decision plane in 4D
- the dissemination plane is now called a control channel (secchan in OpenFlow)