![[network_topologies_study.svg|693]]
## Key concept

**Topology** = the virtual shape of a network, determined by how data moves from one node to another.

The four basic topologies: **Bus · Ring · Star · Tree**

---

## 1. Bus Topology

**How it works:**

- All nodes are **daisy-chained** along the same cable (**backbone**)
- Information sent from a node travels along the backbone until it reaches its destination
- Each end of the cable has a **resistor** to prevent the signal bouncing back

|Advantages|Disadvantages|
|---|---|
|Inexpensive|Damage to main cable → whole network fails/unusable|
|Easy to set up|Slower with many computers (possible collisions)|
|Doesn't require much cable|Every workstation "sees" all data → **security risk**|

---

## 2. Ring Topology

**How it works:**

- Nodes daisy-chained into a **giant ring of cable**
- Data travels in **one direction** (clockwise or counter-clockwise)
- A **token** (code) loops endlessly through the network
- A node grabs the token, replaces it with its data + destination address → message circles the ring until the destination node recognises it

|Advantages|Disadvantages|
|---|---|
|Fast transmission (one direction)|Main cable failure or faulty device → **whole network fails**|
|No risk of data collisions|—|

---

## 3. Star Topology

**How it works:**

- Several nodes linked to a **central device**: hub, switch, or router
- If one cable or device fails → all others continue working

### Central devices compared

|Device|How it works|
|---|---|
|**Hub**|Receives incoming data packets, stores in a **memory buffer** if busy, then sends to **every node** (regardless of address)|
|**Switch**|Like a hub, but knows which connections lead to specific nodes → sends only to **intended nodes**. Faster than a hub. Also handles **broadcast packets** (sent to all)|
|**Router**|Like a switch, but **does NOT accept broadcast packets**. More selective.|

|Advantages|Disadvantages|
|---|---|
|Reliable — one cable failing doesn't affect others|Expensive — uses the **most cable**|
|—|New hubs, switches or routers add extra cost|

---

## 4. Tree Topology (also called Star Bus)

**How it works:**

- Integrates **multiple star topologies onto a bus**
- Nodes in particular areas are connected to hubs (creating stars)
- Hubs are connected together along the **network backbone**

|Advantages|Disadvantages|
|---|---|
|Supports **future expandability**|Installation of new hardware is **very expensive**|
|**Fault tolerant**|Additional cable needed|
|Easy to troubleshoot|—|
|More popular than bus or star|—|

---

## Quick Comparison Table

|Topology|Data path|Fails if...|Cost|Security|
|---|---|---|---|---|
|**Bus**|Linear backbone|Main cable breaks|Low|Weak (all see all data)|
|**Ring**|One direction, loop|Any cable or device fails|Medium|Better|
|**Star**|Central hub/switch/router|Central device fails|High|Good|
|**Tree**|Stars on a bus|Backbone fails|Very high|Good|

---

## Key Vocabulary

|Term|Meaning|
|---|---|
|**Topology**|Virtual shape/structure of a network|
|**Node**|Any device connected to the network|
|**Backbone**|Main cable of the network|
|**Daisy-chain**|Connect devices one after another in sequence|
|**Token**|Code that loops through a ring network|
|**Packet**|Block of data transmitted over a network|
|**Memory buffer**|Temporary storage in a hub for incoming packets|
|**Broadcast**|Packet sent to all nodes simultaneously|
|**Hub**|Central device that sends to all nodes|
|**Switch**|Smarter hub — sends only to intended nodes|
|**Router**|Like a switch, but rejects broadcast packets|
|**Troubleshoot**|Find and eliminate a problem|
|**Grabbing**|Taking hold of something (here: a node grabbing the token)|