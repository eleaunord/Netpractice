# NetPractice – Learn Networking by Doing

## 📋 Project Description

**NetPractice** is a browser-based interactive training project aimed at teaching the **basics of networking** through configuration challenges. The goal is to understand how TCP/IP works, practice subnetting, and manage routing between devices like switches and routers.

> To run the training interface:

```bash
python3 -m http.server
```

> 📌 Note: Levels **ex06 to ex10** are particularly relevant for exams!

---

## 🧠 What I Learned

### How TCP Addressing Works

* **TCP (Transmission Control Protocol)** ensures reliable data transfer by breaking data into packets and managing their delivery.
* Before transmission, TCP establishes a connection between the source and the destination and keeps it alive until the communication ends.

### How IP Addressing Works

* **IP (Internet Protocol)** assigns unique addresses to devices across a network.
* Each IP address consists of:

  * **Network portion**
  * **Host portion**
* These parts are separated using a **subnet mask**.

---

## Subnet Mask & Binary AND

A **subnet mask** is a 32-bit value that distinguishes the network and host parts of an IP address using a **bitwise AND** operation.

Example:

```
IP address : 01101000.11000110.11110001.01111101
Mask       : 11111111.11111111.11111111.10000000
Result     : 01101000.11000110.11110001.00000000 → 104.198.241.0
```

📌 **/25 subnet** means:

* First 25 bits = network
* Last 7 bits = host
* Usable range: 104.198.241.1 to 104.198.241.126

---

## 💡 Range of Host Addresses

From:

```
104.198.241.0 → reserved (network)
104.198.241.127 → reserved (broadcast)
```

➡️ Usable: **104.198.241.1 to 104.198.241.126**

---

## 🔀 CIDR Notation (Classless Inter-Domain Routing)

CIDR represents subnet masks like:

```
/25 = 255.255.255.128 = 11111111.11111111.11111111.10000000
```

* `1` bits → network
* `0` bits → host

---

## 🔌 Network Devices

### 🖧 Switch

* Connects multiple devices within **one** local network.
* Forwards packets **within** its network only.

### 🌐 Router

* Connects multiple networks.
* Requires separate interfaces for each network.
* Interfaces **must not overlap** in address ranges.

---

## 📘 Routing Table Basics

Used to direct packets:

```
Destination: 0.0.0.0/0 (default route)
Next hop  : IP address of the next router or gateway
```

Example:

```
122.3.5.3/24 → Network 122.3.5.0
```

---

## 🧮 Subnetting

### What is /28?

* 255.255.255.240 → 11111111.11111111.11111111.11110000
* 4 bits for host = 2⁴ = 16 IPs per subnet

Out of 16:

* 1 = network address
* 1 = broadcast address
* 14 = usable for hosts

### Subnet Examples:

* **1st subnet**: 93.198.14.0/28 → 93.198.14.1 – 93.198.14.14
* **2nd subnet**: 93.198.14.16/28 → 93.198.14.17 – 93.198.14.30
* **4th subnet**: 93.198.14.64/28 → 93.198.14.65 – 93.198.14.78

Each subnet increments by 16.

---

## Exo Notes

* **/24** = 255.255.255.0
* **Client D** doesn't require explicit routing entry if it relies on the router's **default route**.

---

## 📷 Visual References

<details open>
<summary>Level 8</summary>
<br>

![image](https://github.com/user-attachments/assets/12736457-1fab-4162-889f-78f22d647585)

</details>

<details open>
<summary>Level 9</summary>
<br>

![image](https://github.com/user-attachments/assets/688c66d0-2918-45ff-9d3e-862073d477f8)

![image](https://github.com/user-attachments/assets/b3fcdc92-33a5-41f5-8914-9e3433b746e4)

</details>

---

## ⚙️ Difficulties Faced

* Getting used to **CIDR notation** and converting subnet masks to binary.
* Understanding how subnet boundaries work (especially with /28).
* Figuring out **why certain routes failed** due to overlapping ranges or missing next hops.
* Interpreting **routing tables** and making sense of how the next hop IP should be chosen.
* Remembering to avoid **broadcast** and **network addresses** when assigning IPs.

---

## 🎯 Final Thoughts

NetPractice provided me with a **hands-on introduction to networking**, including:

* How addressing and routing work in real scenarios.
* Practical application of subnetting logic.
* Debugging and validating network setups.

It’s an intuitive and fun way to understand what’s happening behind the scenes when devices communicate over the internet.
