### OpenFlow Protocol Specifications
It separates data & control plane. The controller speaks to the OpenFlow switch over a secure channel and it effectively instructs the OpenFlow switch to update its flow table entries to take different actions on various traffic flows that pass through the switch.
The purpose of the control channel is effectively to update this flow table and all of the logic concerning how the flow table entries are updated are contained at the controller. All of the smarts of the network are resident at the controller and the switches job is simply reduced to forwarding traffic based on the flow table entries that the controller installs.
The OpenFlow protocol specification defines a number of things including the **complements of the switch**, the **message format**, and what **types of actions** the flow table should be capable of performing.

---

### Switch Components
1. **Flow Table**: performs packet lookup. The lookup function compares the fields in each packet to a flow table that resides in the switch and looks for a match (in the header of the packet). The actions that the switch takes then depend on how or whether the packets passing through that switch match any of those particular flow table entries. If there is no match, the traffic is sent to the controller.
2. **Secure Channel**: is how the switch communicates with the external controller.

---

### Matching

When a packet arrives to the switch, it parses the header fields & based on the values of the fields, it tries to match them against flow table entries in any of several flow tables. If there is no match the traffic is sent to the controller, otherwise actions are performed based on the actions specified in the matching flow table entries.
For scalability reasons it does make sense to try to match as many packets as possible in the switch to avoid having too much traffic diverted to the controller. 

In OpenFlow v1.0 there is 12-tuple for 12 fields in packet header on which a flow table entry could match. The fields are:
- incoming switch port
- source and destination MAC address
- Ethernet type
- VLAN ID
- source and destination IP address
- packet protocol (TCP, UDP, etc.)
- TCP source and destination port

---

### Actions

Two mandatory actions in OpenFlow are forwarding the packet & dropping it.
- Forward:
	- ALL: send out traffic to all interfaces (not the incoming interface).
	- CONTROLLER: encapsulate & send to the controller.
	- LOCAL: send to the switch's local networking stack.
	- TABLE: perform actions in flow table (packet-out).
	- IN PORT: send the packet out the input port.
	- Optional: normal forwarding, spanning tree.
- Drop: a flow-entry with no specified action indicates that all matching packets should be dropped. 

There are several optional actions in the specification of OpenFlow v1.0
- Modify: switch might modify various packet header values (e.g. VLAN ID, destination IP address for load balancing). 
- Enqueue: send the packet through a queue attached to a port (QoS, traffic shaping).

---

### Example: dpctl Control Channel
A switch by default listens to a port for controller, but when there is none we can talk to the switch using **dpctl**. It allows us to perform operations such as inspecting the flow table entries on the switch, modifying flow table entries and so forth.

```bash
$ dpctl show tcp:127.0.0.1:6634
$ dpctl dump-flows tcp:127.0.0.1:6634
$ dpctl add-flow tcp:127.0.0.1:6634 in_port=1,actions=output:2
```

---

### OpenFlow (v1.3) Enhancements 
- Action Set: set of actions to be performed on each packet
- Group: a list of actions sets
- Each table can update fields & modify action set in pipeline

There is an option to execute all of the action sets in a particular group, like for multicast and cloning the packet. **Indirect group** is when one actions set is executed, useful for pointing multiple flow entries to a common action.

Example Actions:
- TTL: decrement, copy
- MPLS
- QoS

---

### Other SDN Control Architectures
- RCP
- Juniper's Contrail Controller
	- XMPP as control plane
	- L2 & L3 virtual networks
	- ODL
- Cisco's Open Network Environment
	- centralized software controller
	- programmable data plane
	- virtual overlays