![[internet_protocols_study.svg|633]]
## The Internet = Packet-Switched Network

When you send information across the Internet, the data is **broken into small packets**. A series of **routers** sends each packet across the Net **individually**. After arriving at the receiving computer, the packets are **recombined into their original, unified form**.

This job is handled by two protocols: **TCP** and **IP** — commonly referred to as **TCP/IP**.

---

## The Two Protocols

### TCP — Transmission Control Protocol

- Breaks data into packets
- Calculates and adds **checksum** to each packet header
- Reassembles packets at the destination
- Detects corruption and requests retransmission

### IP — Internet Protocol

- Puts each packet into a separate **envelope** with addressing information
- Tells the Internet (4) **where** to send the data
- Routers examine the IP envelopes and determine the most **(5) efficient** path

---

## How TCP Works — Step by Step

1. Data broken into packets of **fewer than 1,500 characters** each
2. TCP creates each packet, adds a **header**, and calculates a **checksum** — a number used to detect errors introduced during transmission
3. Each packet placed in an **IP envelope** with addressing info → routers determine most efficient path to next router closest to final destination
4. Packets travel through a series of routers — may arrive **(6) out of order** (traffic load on the Net changes constantly)
5. On arrival: TCP calculates a checksum for each packet and **compares it with the one sent in the packet**
    - If checksums **match** → packet is intact
    - If checksums **don't match** → data was corrupted **(7) during** transmission → packet discarded and original asked to be **retransmitted**
6. If non-corrupt packets received → TCP **reassembles** them into the original, unified form

---

## Gap-Fill Answers (Exercise 9)

|Gap|Answer|
|---|---|
|(1)|at|
|(2)|than|
|(3)|which / this|
|(4)|where|
|(5)|most|
|(6)|out|
|(7)|during|
|(8)|There|

---

## IPv4 vs IPv6

|Feature|IPv4|IPv6|
|---|---|---|
|First used|1981|1999|
|Address size|32-bit|128-bit|
|Format|4 groups of decimal numbers|8 groups of hexadecimal digits|
|Example|192.168.1.1|2001:0db8:85a3:0000:0000:8a2e:0370:7334|
|Total addresses|~4.3 billion|~340 undecillion|

**Why IPv6?** IPv4's address pool was almost exhausted — the rapid growth of the Internet required a vastly larger address space.

---

## Key Vocabulary

|Term|Meaning|
|---|---|
|**Packet**|Small chunk of data sent individually across the network|
|**Packet-switched**|Network where data travels in separate packets via any available route|
|**TCP**|Transmission Control Protocol — manages packet creation and reassembly|
|**IP**|Internet Protocol — manages addressing and routing|
|**Checksum**|Mathematical sum used to detect whether data was corrupted during transmission|
|**Header**|Block of metadata attached to each packet|
|**Router**|Device that forwards packets toward their destination|
|**Corrupt**|Data that has been scrambled or damaged during transmission|
|**Retransmit**|Send a packet again after detecting corruption|
|**Envelope (IP)**|Wrapper containing addressing information for each packet|
|**Unified form**|The original, complete, reassembled message|