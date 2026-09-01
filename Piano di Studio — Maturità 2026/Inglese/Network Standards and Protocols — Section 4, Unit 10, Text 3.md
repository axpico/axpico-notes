---
subject: inglese
tags:
  - inglese
  - network
  - protocolli
  - maturita-2026
---
![[osi_model_study.svg|677]]
## Key Definitions

### Standard

An **agreed method** that determines how data is sent and received.

### Protocol

The **formal rules and procedures** that need to be followed to allow data to be **transmitted, received, and correctly interpreted**.

### OSI Model (Open Systems Interconnection)

- Developed in **1984** by the **ISO** (International Standards Organization)
- ISO = global federation of national standards organizations representing **~130 countries**
- OSI is **NOT** a communication standard — it is a **guideline for developing** such standards
- Consists of **7 layers** arranged in a **protocol stack**

### Protocol stack

A **layered model** where each layer contains a subset of the functions required to control network communications. At each layer, **additional information (headers) is added**.

---

## The 7 OSI Layers (top → bottom when sending)

### Layer 7 — Application layer

- The **only layer that provides service directly to the end user**
- Converts a message's data into bits
- Attaches a **header** identifying the sending and receiving computers

### Layer 6 — Presentation layer

- **Translates** the message into a language the receiving computer can understand (often **ASCII**)
- **Compresses and encrypts** the data
- Adds a header specifying the language, compression, and encryption schemes

### Layer 5 — Session layer

- **Opens communications**
- Sets **brackets** for the beginning and end of the message
- Establishes whether the message will be sent as:
    - **Half duplex** — each computer takes turns sending and receiving
    - **Full duplex** — both computers send and receive at the same time

### Layer 4 — Transport layer

- **Protects the data** being sent
- **Subdivides data into segments**
- Creates **checksum tests** (mathematical sums based on data contents) to detect if data was scrambled
- Makes **backup copies** of the data
- The **header** identifies each segment's checksum and its position in the message

### Layer 3 — Network layer

- **Selects a route** for the message
- **Forms segments into packets**, counts them
- Adds a header containing the **sequence of packets** and the **address of the receiving computer**

### Layer 2 — Data link layer

- **Supervises the transportation**
- **Confirms the checksum** and then addresses and duplicates the packets
- Keeps a **copy of each packet** until it receives confirmation from the next point that the packet arrived **undamaged**

### Layer 1 — Physical layer

- **Encodes packets** into the medium that will carry them (e.g. analogue signal for a telephone line)
- **Sends the packet** along that medium

---

## Receiving Process

At the receiving node, the entire layered process is **reversed**:

- Message reconverted into bits
- Checksum recalculated
- Packets recounted
- Message reassembled

---

## Key Vocabulary

|Term|Meaning|Italian|
|---|---|---|
|**Layer**|One level of the OSI stack|livello|
|**Protocol**|Formal rules for data transmission|protocollo|
|**Standard**|Agreed method for sending/receiving data|standard|
|**Protocol stack**|All 7 layers together|—|
|**Header**|Block of metadata added at each layer|intestazione|
|**Checksum**|Mathematical sum used to verify data integrity|somma di controllo|
|**Half duplex**|Computers take turns transmitting|trasmissione bidirezionale alternata|
|**Full duplex**|Both computers transmit simultaneously|trasmissione bidirezionale simultanea|
|**Packet**|Unit of data at the network layer|pacchetto|
|**Segment**|Unit of data at the transport layer|segmento|
|**Encrypt**|Encode data for security|cifrare|
|**ASCII**|Standard encoding system for text characters|—|

---

## Layer Functions — Quick Reference (for Exercise 8)

|Function|Layer|
|---|---|
|Transmits bits (ones and zeros)|Physical (1)|
|Responsible for routing packets across the network|Network (3)|
|Responsible for splitting data into segments|Transport (4)|
|Converts message to bits, attaches sender/receiver header|Application (7)|
|Compresses and encrypts data|Presentation (6)|
|Confirms checksum, keeps packet copy until arrival confirmed|Data link (2)|
|Sets half/full duplex, opens/closes communication|Session (5)|