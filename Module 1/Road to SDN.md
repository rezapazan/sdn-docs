**Three Stages:**
1. Active Networking: programmable networks
2. control & data plane separation: open interfaces between planes
3. OpenFlow API & Network OSs: widespread adoption of open interfaces

---

### Active Networks:
It came at the time of internet's diverse applications & greater use. It was the first attempt to make networks programmable. It was pushed by reduction in computing costs (Tech push) on the other hand deployment challenges (Use pull).

**Contributions:**
1. programmable functions
2. network virtualization
3. demultiplexing to software programs
4. offering a unified vision for middlebox orchestration

**myth:**
1. end-users must program packets: rare model
2. packets must carry java code: programmable model

---

### Control/Data plane separation:
- attempt to solve traffic engineering problems
- tech push: open interfaces (e.g. ForCES), centralized control (e.g. RCP)
- use pull: network management problems

**Contributions:**
1. centralized control with open interfaces to routers & switches
2. distributed state management

**Myths ???**

---

### OpenFlow:
It is more general with more functions building on switch hardware. It has more limited flexibility, but immediate deployment. 
- open storm between vendors etc. (Tech push)
- use pull: first in campuses then data centers

**Contributions:**
1. generalizing network devices & functions
2. the vision of network operating system:
	- data plane
	- state management
	- control logic
3. distributed management

**Myths:**
1. first packet must go to controller: no assumptions or weather handling the traffic
2. controller must be physically centralized: deployments have distributed controllers.
3. SDN is OpenFlow: OpenFlow is one instantiation of SDN