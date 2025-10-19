Network Topologies & LAN Fundamentals 🌐
========================================

English Version
---------------

* * *

### What is Network Topology?

In networking, the term **"topology"** refers to the structure or layout of a network. It describes how devices are physically or logically arranged and connected to each other in a **Local Area Network (LAN)**.

**Key Concept:** Topology defines both the physical layout (cables, connections) and logical flow (data transmission) in a network.

* * *

Network Topologies 🔗
---------------------

### 1. Star Topology ⭐

The **Star Topology** is the most common network design today. Devices connect individually through a central network device, such as a **switch** or **hub**.

**Structure:**
        Device 1
            |
    Device 2 -- Switch -- Device 4
            |
        Device 3

**Advantages:**

* ✅ **Highly scalable** - easy to add new devices
* ✅ **Easy to manage** - centralized control
* ✅ **Fault isolation** - one device failure doesn't affect others
* ✅ **High performance** - dedicated bandwidth per device
* ✅ **Most reliable** topology

**Disadvantages:**

* ❌ **Expensive** - requires more cabling and specialized equipment
* ❌ **Single point of failure** - if central device fails, entire network goes down
* ❌ **Maintenance intensive** - larger networks require more upkeep
* ❌ **Difficult troubleshooting** - complexity increases with scale

**Best For:**

* Corporate networks
* Modern home networks
* Any network requiring reliability and scalability

**Common Central Devices:**

* 🔷 **Switch** (most common, intelligent)
* 🔷 **Hub** (older, less efficient)
* 🔷 **Router** (for connecting multiple networks)

* * *

### 2. Bus Topology 🚌

**Bus Topology** relies on a single connection called the **backbone cable**. All devices connect to this single cable, similar to leaves branching from a tree.

**Structure:**
    Device 1 -- Device 2 -- Device 3 -- Device 4
                (Backbone Cable)

**How It Works:**

* All data travels along the same cable
* Each device receives all transmissions
* Devices only process data meant for them

**Advantages:**

* ✅ **Very cheap** - minimal cabling required
* ✅ **Simple to set up** - easy installation
* ✅ **No specialized equipment** needed
* ✅ **Good for small networks**

**Disadvantages:**

* ❌ **Performance degrades** quickly with multiple devices
* ❌ **Network congestion** - all data uses same cable
* ❌ **Difficult troubleshooting** - hard to identify problematic device
* ❌ **No redundancy** - backbone cable failure kills entire network
* ❌ **Security concerns** - all devices see all traffic
* ❌ **Limited cable length**

**Best For:**

* Small, temporary networks
* Testing environments
* Legacy systems (rarely used today)

**Obsolete Technology:** Bus topology is largely outdated and replaced by Star topology in modern networks.

* * *

### 3. Ring Topology 🔄

In **Ring Topology**, devices connect directly to each other, forming a closed loop or "ring". Data travels in one direction (or both in dual-ring) around the ring.

**Structure:**
        Device 1
       /        \
    Device 4    Device 2
       \        /
        Device 3

**How It Works:**

* Data travels from device to device around the ring
* Each device acts as a repeater, forwarding data
* A device only sends its own data if it has data to send
* Otherwise, it forwards data from other devices

**Advantages:**

* ✅ **Minimal cabling** required
* ✅ **Less dependent** on specialized hardware
* ✅ **Easy troubleshooting** - predictable data path
* ✅ **No data collisions** - orderly data transmission
* ✅ **Fair access** - each device gets equal opportunity

**Disadvantages:**

* ❌ **Inefficient data transmission** - data may pass through many devices
* ❌ **Single point of failure** - one broken cable or device kills entire network
* ❌ **Adding/removing devices** disrupts network
* ❌ **Slower than Star** topology

**Best For:**

* Small office networks
* Token Ring networks (legacy)
* Fiber Distributed Data Interface (FDDI)

**Modern Usage:** Less common today, but still used in some industrial and legacy systems.

* * *

Network Topology Comparison Table 📊
------------------------------------

| Feature             | Star ⭐                       | Bus 🚌           | Ring 🔄 |
| ------------------- | ---------------------------- | ---------------- | ------- |
| **Cost**            | High                         | Low              | Medium  |
| **Scalability**     | Excellent                    | Poor             | Medium  |
| **Performance**     | High                         | Degrades quickly | Medium  |
| **Reliability**     | High (except central device) | Low              | Low     |
| **Troubleshooting** | Difficult (large networks)   | Very difficult   | Easy    |
| **Cable Required**  | Most                         | Least            | Medium  |
| **Redundancy**      | Medium                       | None             | None    |
| **Modern Usage**    | Very common                  | Obsolete         | Rare    |

* * *

Network Devices 🔧
------------------

### Switches 🔀

**Switches** are specialized networking devices designed to connect multiple devices using Ethernet. They are the backbone of modern networks.

**Key Features:**

* 📌 Operates at **Layer 2** (Data Link Layer)
* 📌 Uses **MAC addresses** to forward data
* 📌 Available in various port counts: 4, 8, 16, 24, 32, 64 ports
* 📌 **Intelligent** - tracks which device is on which port

**How Switches Work:**

1. **Learns MAC addresses** - builds a MAC address table
2. **Forwards intelligently** - sends data only to destination port
3. **Reduces network traffic** - no unnecessary broadcasting

**Switches vs Hubs:**

| Feature          | Switch                      | Hub                          |
| ---------------- | --------------------------- | ---------------------------- |
| **Intelligence** | Smart - knows MAC addresses | Dumb - broadcasts everything |
| **Efficiency**   | High - targeted delivery    | Low - floods all ports       |
| **Performance**  | Fast                        | Slow (collisions)            |
| **Security**     | Better - isolated traffic   | Poor - all see all traffic   |
| **Cost**         | Higher                      | Lower                        |
| **OSI Layer**    | Layer 2                     | Layer 1                      |

**Example:**
    When Device A sends data to Device C:
    - Hub: sends to all ports (B, C, D all receive)
    - Switch: sends only to port where C is connected

**Redundancy:**

* ✅ Multiple switches can be interconnected
* ✅ Creates multiple paths for data
* ✅ If one path fails, another is available
* ⚠️ May slightly reduce performance due to longer paths

* * *

### Routers 🗺️

**Routers** connect different networks and route data between them. They operate at **Layer 3** (Network Layer) using **IP addresses**.

**Key Functions:**

* 🌐 **Connects networks** - links different LANs or connects to the Internet
* 🗺️ **Routes data** - determines best path between networks
* 🔒 **Provides security** - acts as gateway between networks
* 📡 **NAT** - translates private IP addresses to public

**Routing Process:**

1. Receives packet with destination IP address
2. Checks routing table for best path
3. Forwards packet to next hop
4. Repeats until packet reaches destination

**Router vs Switch:**

| Feature          | Router                     | Switch                          |
| ---------------- | -------------------------- | ------------------------------- |
| **OSI Layer**    | Layer 3 (Network)          | Layer 2 (Data Link)             |
| **Uses**         | IP addresses               | MAC addresses                   |
| **Purpose**      | Connect different networks | Connect devices in same network |
| **Scope**        | WAN/Internet               | LAN                             |
| **Intelligence** | High - routing decisions   | Medium - MAC learning           |

**Routing Benefits:**

* ✅ Enables communication between different networks
* ✅ Creates multiple paths for data delivery
* ✅ Provides fault tolerance
* ✅ Increases network reliability

* * *

Subnetting 🔢
-------------

**Subnetting** is the practice of dividing a network into smaller sub-networks (subnets). It allows network administrators to organize and manage networks efficiently.

**Why Use Subnets?**

* 🎯 **Efficiency** - better use of IP address space
* 🔒 **Security** - isolate different departments/functions
* 📊 **Management** - easier to organize and control
* ⚡ **Performance** - reduce broadcast traffic

**Real-World Example:** A café has two separate networks:

1. **Employee Network** - for staff, registers, internal devices
2. **Guest Network** - public Wi-Fi for customers

Both networks are isolated but can still access the Internet.

* * *

### IP Address Components

An **IP address** consists of **4 octets** (32 bits), each ranging from **0 to 255**.

**Example:** `192.168.1.100`

A **subnet mask** also has 4 octets and determines which part is network and which is host.

**Common Subnet Masks:**

* `255.255.255.0` (/24) - 254 hosts
* `255.255.0.0` (/16) - 65,534 hosts
* `255.255.255.128` (/25) - 126 hosts

* * *

### Three Key Addresses in Subnetting

#### 1. Network Address 🌐

**Purpose:** Identifies the start of the network. Represents the network itself.

**Characteristics:**

* ✅ First address in the subnet
* ✅ Cannot be assigned to a device
* ✅ Used for routing identification

**Example:**

* Device IP: `192.168.1.100`
* Network Address: `192.168.1.0`

* * *

#### 2. Host Address 💻

**Purpose:** Identifies individual devices within the subnet.

**Characteristics:**

* ✅ Unique address for each device
* ✅ Can be any address between network and broadcast
* ✅ Used for device-to-device communication

**Example:**

* Device 1: `192.168.1.10`
* Device 2: `192.168.1.25`
* Device 3: `192.168.1.100`

* * *

#### 3. Default Gateway Address 🚪

**Purpose:** Special address for the device that can send data to other networks (usually a router).

**Characteristics:**

* ✅ Acts as "exit point" from the subnet
* ✅ Usually first (`.1`) or last (`.254`) address
* ✅ Required for Internet access
* ✅ All devices in subnet must know this address

**Example:**

* Network: `192.168.1.0/24`
* Default Gateway: `192.168.1.1` or `192.168.1.254`
* Hosts: `192.168.1.2` to `192.168.1.253`

**How It Works:**
    Device (192.168.1.100) wants to reach Internet (8.8.8.8)
        ↓
    Sends packet to Default Gateway (192.168.1.1)
        ↓
    Gateway (Router) forwards to Internet

* * *

ARP Protocol (Address Resolution Protocol) 🔍
---------------------------------------------

**ARP** is a protocol that allows devices to discover the **MAC address** associated with an **IP address** on the local network.

**Why ARP is Needed:**

* IP addresses (logical) are used for routing
* MAC addresses (physical) are used for actual delivery
* ARP bridges the gap between these two

* * *

### How ARP Works

**ARP Cache:** Each device maintains an **ARP cache** - a table storing IP-to-MAC mappings.

**Example ARP Cache:**
    IP Address       MAC Address           Age
    192.168.1.1      AA:BB:CC:DD:EE:FF     120s
    192.168.1.50     11:22:33:44:55:66     45s
    192.168.1.100    FF:EE:DD:CC:BB:AA     200s

* * *

### ARP Process: Two Message Types

#### 1. ARP Request (Broadcast) 📢

When a device needs to communicate but doesn't know the MAC address:

**Process:**

1. Device A wants to send data to `192.168.1.100`
2. Checks ARP cache - MAC address not found
3. Sends **ARP Request** broadcast to entire network
4. Request asks: "Who has IP `192.168.1.100`? Tell `192.168.1.50`"

**ARP Request Details:**

* 📡 Sent to **broadcast MAC** address: `FF:FF:FF:FF:FF:FF`
* 📡 ALL devices on network receive it
* 📡 Only target device responds

* * *

#### 2. ARP Reply (Unicast) 📥

The device with matching IP responds:

**Process:**

1. Device with `192.168.1.100` receives ARP Request
2. Recognizes its own IP address
3. Sends **ARP Reply** directly to requesting device
4. Reply contains: "I am `192.168.1.100`, my MAC is `AA:BB:CC:DD:EE:FF`"

**ARP Reply Details:**

* 📨 Sent directly (unicast) to requesting device
* 📨 Contains MAC address of target
* 📨 Requesting device updates its ARP cache

* * *

### Complete ARP Example

    Step 1: Device A (192.168.1.50) wants to talk to Device B (192.168.1.100)
    
    Step 2: ARP Request (Broadcast)
    From: 192.168.1.50 (MAC: 11:22:33:44:55:66)
    To: 255.255.255.255 (MAC: FF:FF:FF:FF:FF:FF)
    Message: "Who has 192.168.1.100? Tell 192.168.1.50"
    
    Step 3: All devices receive, only 192.168.1.100 responds
    
    Step 4: ARP Reply (Unicast)
    From: 192.168.1.100 (MAC: AA:BB:CC:DD:EE:FF)
    To: 192.168.1.50 (MAC: 11:22:33:44:55:66)
    Message: "I am 192.168.1.100, my MAC is AA:BB:CC:DD:EE:FF"
    
    Step 5: Device A updates ARP cache and begins communication

* * *

### Key ARP Concepts

**Remember:**

* 🔑 **MAC addresses** = Physical identifiers (hardware)
* 🔑 **IP addresses** = Logical identifiers (software)
* 🔑 **ARP** = Translates IP → MAC for local network communication

**ARP Cache Timeout:**

* Entries expire after certain time (typically 2-20 minutes)
* Prevents stale entries
* Forces refresh of MAC addresses

* * *

DHCP Protocol (Dynamic Host Configuration Protocol) 🔄
------------------------------------------------------

**DHCP** automatically assigns IP addresses to devices on a network, eliminating the need for manual configuration.

**Without DHCP:** Network admin must manually configure each device's IP address  
**With DHCP:** Devices automatically receive IP configuration when connecting

* * *

### DHCP Components

**DHCP Server:**

* 🖥️ Manages pool of available IP addresses
* 🖥️ Assigns addresses to requesting devices
* 🖥️ Tracks which addresses are in use
* 🖥️ Can be router, dedicated server, or network appliance

**DHCP Client:**

* 💻 Any device requesting IP address
* 💻 Computers, phones, printers, IoT devices

* * *

### The DHCP Process: DORA 🎭

DHCP uses a **4-step process** known as **DORA**:

#### 1. **D**HCP Discover 🔍

**Client broadcasts:** "Is there a DHCP server on this network?"

**Details:**

* 📡 Broadcast message (255.255.255.255)

* 📡 Client has no IP yet, uses `0.0.0.0`

* 📡 Sent when device first connects to network
    Client: "Hello! I need an IP address. Any DHCP servers out there?"
    Destination: 255.255.255.255 (broadcast)
    Source: 0.0.0.0 (no IP yet)

* * *

#### 2. **O**ffer 🎁

**Server responds:** "I can offer you this IP address!"

**Details:**

* 📨 DHCP server responds with available IP

* 📨 Includes IP address, subnet mask, gateway, DNS

* 📨 Multiple DHCP servers may respond

* 📨 Client typically accepts first offer
    DHCP Server: "You can use 192.168.1.100!"
    Offered IP: 192.168.1.100
    Subnet Mask: 255.255.255.0
    Gateway: 192.168.1.1
    DNS: 8.8.8.8
    Lease Time: 24 hours

* * *

#### 3. **R**equest 📋

**Client responds:** "Yes, I want that IP address!"

**Details:**

* 📡 Client broadcasts acceptance (other servers need to know)

* 📡 Formally requests the offered IP

* 📡 Declines other offers (if multiple servers responded)
    Client: "I accept the offer of 192.168.1.100 from Server X"
    Destination: 255.255.255.255 (broadcast)
    Requested IP: 192.168.1.100

* * *

#### 4. **A**cknowledge (ACK) ✅

**Server confirms:** "Confirmed! You can use this IP address now."

**Details:**

* ✅ Final confirmation from server

* ✅ Provides lease duration

* ✅ Device can now use IP address

* ✅ Communication complete
    DHCP Server: "Confirmed! 192.168.1.100 is yours for 24 hours"
    Status: ACK
    IP Assigned: 192.168.1.100
    Valid Until: Tomorrow at this time

* * *

### DHCP DORA Diagram

    Client                                  DHCP Server
      |                                          |
      |------ 1. DHCP Discover (Broadcast) ---->| "Anyone have IP for me?"
      |                                          |
      |<----- 2. DHCP Offer -------------------|  "Here's 192.168.1.100"
      |                                          |
      |------ 3. DHCP Request (Broadcast) ----->| "I'll take that IP!"
      |                                          |
      |<----- 4. DHCP ACK ---------------------|  "Confirmed!"
      |                                          |
      [Device now has IP: 192.168.1.100]

* * *

### DHCP Lease Information

**What Client Receives:**

* 📍 **IP Address** - unique address for the device
* 📍 **Subnet Mask** - defines network size
* 📍 **Default Gateway** - router IP for Internet access
* 📍 **DNS Servers** - for domain name resolution
* 📍 **Lease Duration** - how long IP is valid

**Typical Lease Times:**

* Home networks: 24 hours to 7 days
* Corporate networks: 8 hours to 24 hours
* Public Wi-Fi: 30 minutes to 2 hours

* * *

### DHCP Lease Renewal

**Process:**

1. Client uses IP for lease duration
2. At 50% of lease time, client attempts renewal
3. If renewal fails, tries again at 87.5% of lease
4. If still fails, must start DORA process again

**Example:**

* Lease duration: 24 hours
* Renewal attempt 1: After 12 hours (50%)
* Renewal attempt 2: After 21 hours (87.5%)
* If both fail: Start DORA again after 24 hours

* * *

### DHCP Advantages & Disadvantages

**Advantages:**

* ✅ **Automatic configuration** - no manual setup
* ✅ **Centralized management** - easy to manage IP addresses
* ✅ **Prevents conflicts** - no duplicate IPs
* ✅ **Efficient use** of IP address space
* ✅ **Easy to scale** - add devices without reconfiguration

**Disadvantages:**

* ❌ **Single point of failure** - if DHCP server down, new devices can't connect
* ❌ **Network traffic** - DHCP messages use bandwidth
* ❌ **Security concerns** - rogue DHCP servers possible
* ❌ **Changing IP addresses** - can complicate certain applications

* * *

### Static vs Dynamic IP Assignment

| Feature           | Static IP                          | Dynamic IP (DHCP)   |
| ----------------- | ---------------------------------- | ------------------- |
| **Configuration** | Manual                             | Automatic           |
| **Management**    | Complex (large networks)           | Simple              |
| **IP Conflicts**  | Possible                           | Prevented           |
| **Best For**      | Servers, printers, network devices | End-user devices    |
| **Reliability**   | High (doesn't change)              | Medium (can change) |
| **Flexibility**   | Low                                | High                |

**When to Use Static:**

* 🖥️ Servers
* 🖨️ Printers
* 🔧 Network equipment (switches, routers)
* 📹 IP cameras
* 🎮 Gaming consoles (port forwarding)

**When to Use DHCP:**

* 💻 Laptops
* 📱 Smartphones
* 🖥️ Desktop computers
* 📺 Smart TVs
* 🏠 IoT devices

* * *

Practical Commands for Network Administration 💻
------------------------------------------------

### View DHCP-assigned IP (Windows):

    ipconfig /all

### View DHCP-assigned IP (Linux/Mac):

    ifconfig
    # or
    ip addr show

### Renew DHCP lease (Windows):

    ipconfig /release
    ipconfig /renew

### Renew DHCP lease (Linux):

    sudo dhclient -r  # release
    sudo dhclient     # renew

### View ARP cache (Windows/Linux/Mac):

    arp -a

### Clear ARP cache (Windows):

    arp -d

### Clear ARP cache (Linux):

    sudo ip -s -s neigh flush all

### Add static ARP entry:

    # Windows
    arp -s 192.168.1.100 AA-BB-CC-DD-EE-FF
    
    # Linux
    sudo arp -s 192.168.1.100 AA:BB:CC:DD:EE:FF

* * *

Network Topology Best Practices 📋
----------------------------------

### Choosing the Right Topology:

**Star Topology** - Choose when:

* ✅ Budget allows for quality equipment
* ✅ Reliability is critical
* ✅ Network will grow over time
* ✅ Performance is important

**Bus Topology** - Choose when:

* ✅ Temporary or test network
* ✅ Very tight budget
* ✅ Small number of devices (< 5)
* ⚠️ Not recommended for production

**Ring Topology** - Choose when:

* ✅ Legacy system requires it
* ✅ Token Ring network
* ✅ Fair access is priority
* ⚠️ Rarely used in modern networks

* * *

Troubleshooting Network Issues 🔧
---------------------------------

### General Troubleshooting Steps:

1. **Check Physical Connections**
   
   * Are cables plugged in?
   * Are link lights on?
   * Try different cable/port

2. **Verify IP Configuration**
      ipconfig /all  # Windows
      ip addr show   # Linux

3. **Check DHCP**
   
   * Is DHCP server running?
   * Are there available addresses?
   * Try manual IP assignment

4. **Test Local Connectivity**
      ping 192.168.1.1  # Gateway

5. **Check ARP**
      arp -a  # View ARP cache

6. **Test External Connectivity**
      ping 8.8.8.8  # Google DNS

7. **Verify DNS**
      nslookup google.com
   
   

* * *

Security Considerations 🔒
--------------------------

### ARP Security Issues:

**ARP Spoofing Attack:**

* 🔴 Attacker sends fake ARP replies
* 🔴 Redirects traffic through attacker's machine
* 🔴 Man-in-the-middle attack possible

**Protection:**

* 🛡️ Use **Dynamic ARP Inspection** (DAI) on switches
* 🛡️ Static ARP entries for critical devices
* 🛡️ Network monitoring tools

### DHCP Security Issues:

**Rogue DHCP Server:**

* 🔴 Unauthorized DHCP server on network
* 🔴 Can assign malicious gateway/DNS
* 🔴 Intercept or redirect traffic

**Protection:**

* 🛡️ **DHCP Snooping** on switches
* 🛡️ Authorized DHCP servers only
* 🛡️ Port security

**DHCP Starvation Attack:**

* 🔴 Attacker requests all available IPs
* 🔴 Legitimate users can't get addresses
* 🔴 Denial of service

**Protection:**

* 🛡️ Rate limiting on DHCP requests
* 🛡️ Sufficient IP address pool
* 🛡️ Monitor DHCP logs

* * *

Summary: Key Concepts 🎯
------------------------

### Network Topologies:

1. **Star** ⭐ - Most common, reliable, expensive
2. **Bus** 🚌 - Obsolete, cheap, unreliable
3. **Ring** 🔄 - Legacy, fair access, single point of failure

### Network Devices:

1. **Switches** 🔀 - Connect devices in same network (Layer 2)
2. **Routers** 🗺️ - Connect different networks (Layer 3)

### IP Configuration:

1. **Network Address** 🌐 - Identifies the network
2. **Host Address** 💻 - Identifies individual devices
3. **Default Gateway** 🚪 - Exit point to other networks

### Protocols:

1. **ARP** 🔍 - Maps IP addresses to MAC addresses
2. **DHCP** 🔄 - Automatically assigns IP addresses (DORA process)

### Remember:

* 🔑 **MAC = Physical**, **IP = Logical**
* 🔑 **ARP = Local network** communication
* 🔑 **DHCP = Automatic** IP configuration
* 🔑 **Gateway = Exit** to other networks

* * *

Топологии локальных сетей и основы LAN 🌐
=========================================

Русская версия
--------------

* * *

### Что такое топология сети?

В сетевых технологиях термин **"топология"** означает структуру или внешний вид сети. Он описывает, как устройства физически или логически расположены и соединены друг с другом в **локальной сети (LAN)**.

**Ключевая концепция:** Топология определяет как физическую компоновку (кабели, соединения), так и логический поток (передачу данных) в сети.

* * *

Сетевые топологии 🔗
--------------------

### 1. Звездообразная топология ⭐

**Звездообразная топология** — это наиболее распространенный дизайн сетей сегодня. Устройства подключаются индивидуально через центральное сетевое устройство, такое как **коммутатор** или **концентратор**.

**Структура:**
        Устройство 1
            |
    Устройство 2 -- Коммутатор -- Устройство 4
            |
        Устройство 3

**Преимущества:**

* ✅ **Высокая масштабируемость** - легко добавлять новые устройства
* ✅ **Удобное управление** - централизованный контроль
* ✅ **Изоляция сбоев** - отказ одного устройства не влияет на другие
* ✅ **Высокая производительность** - выделенная полоса пропускания для каждого устройства
* ✅ **Самая надежная** топология

**Недостатки:**

* ❌ **Дорогая** - требует больше кабелей и специализированного оборудования
* ❌ **Единая точка отказа** - при выходе из строя центрального устройства вся сеть падает
* ❌ **Требует обслуживания** - более крупные сети нуждаются в большем уходе
* ❌ **Сложная диагностика** - сложность увеличивается с масштабом

**Идеальна для:**

* Корпоративных сетей
* Современных домашних сетей
* Любой сети, требующей надежности и масштабируемости

**Распространенные центральные устройства:**

* 🔷 **Коммутатор** (наиболее распространен, интеллектуальный)
* 🔷 **Концентратор** (устаревший, менее эффективный)
* 🔷 **Маршрутизатор** (для соединения нескольких сетей)

* * *

### 2. Шинная топология 🚌

**Шинная топология** основана на единственном соединении, называемом **магистральным кабелем**. Все устройства подключаются к этому единственному кабелю, подобно листьям, отходящим от дерева.

**Структура:**
    Устройство 1 -- Устройство 2 -- Устройство 3 -- Устройство 4
                  (Магистральный кабель)

**Как это работает:**

* Все данные передаются по одному и тому же кабелю
* Каждое устройство получает все передачи
* Устройства обрабатывают только данные, предназначенные для них

**Преимущества:**

* ✅ **Очень дешевая** - требуется минимум кабелей
* ✅ **Простая установка** - легкий монтаж
* ✅ **Не требует специального оборудования**
* ✅ **Хороша для малых сетей**

**Недостатки:**

* ❌ **Производительность быстро снижается** при увеличении устройств
* ❌ **Перегрузка сети** - все данные используют один кабель
* ❌ **Сложная диагностика** - трудно определить проблемное устройство
* ❌ **Нет резервирования** - отказ магистрального кабеля убивает всю сеть
* ❌ **Проблемы безопасности** - все устройства видят весь трафик
* ❌ **Ограниченная длина кабеля**

**Идеальна для:**

* Малых временных сетей
* Тестовых окружений
* Устаревших систем (сегодня редко используется)

**Устаревшая технология:** Шинная топология в значительной степени устарела и заменена звездообразной топологией в современных сетях.

* * *

### 3. Кольцевая топология 🔄

В **кольцевой топологии** устройства подключаются напрямую друг к другу, образуя замкнутое кольцо или "петлю". Данные передаются в одном направлении (или в обоих направлениях в двойном кольце) по кольцу.

**Структура:**
        Устройство 1
       /        \
    Устройство 4    Устройство 2
       \        /
        Устройство 3

**Как это работает:**

* Данные передаются от устройства к устройству по кольцу
* Каждое устройство действует как повторитель, пересылая данные
* Устройство отправляет свои данные только если у него есть данные для отправки
* В противном случае оно пересылает данные от других устройств

**Преимущества:**

* ✅ **Минимальные требования к кабелям**
* ✅ **Меньшая зависимость** от специализированного оборудования
* ✅ **Легкая диагностика** - предсказуемый путь данных
* ✅ **Нет коллизий данных** - упорядоченная передача данных
* ✅ **Справедливый доступ** - каждое устройство получает равные возможности

**Недостатки:**

* ❌ **Неэффективная передача данных** - данные могут проходить через множество устройств
* ❌ **Единая точка отказа** - один поврежденный кабель или устройство выводит из строя всю сеть
* ❌ **Добавление/удаление устройств** нарушает работу сети
* ❌ **Медленнее звездообразной** топологии

**Идеальна для:**

* Малых офисных сетей
* Сетей Token Ring (устаревшие)
* Fiber Distributed Data Interface (FDDI)

**Современное использование:** Менее распространена сегодня, но все еще используется в некоторых промышленных и устаревших системах.

* * *

Сравнительная таблица топологий 📊
----------------------------------

| Характеристика             | Звезда ⭐                                | Шина 🚌          | Кольцо 🔄   |
| -------------------------- | --------------------------------------- | ---------------- | ----------- |
| **Стоимость**              | Высокая                                 | Низкая           | Средняя     |
| **Масштабируемость**       | Отличная                                | Плохая           | Средняя     |
| **Производительность**     | Высокая                                 | Быстро снижается | Средняя     |
| **Надежность**             | Высокая (кроме центрального устройства) | Низкая           | Низкая      |
| **Диагностика**            | Сложная (большие сети)                  | Очень сложная    | Легкая      |
| **Требуется кабелей**      | Больше всего                            | Меньше всего     | Средне      |
| **Резервирование**         | Среднее                                 | Отсутствует      | Отсутствует |
| **Современное применение** | Очень распространена                    | Устаревшая       | Редкая      |

* * *

Сетевые устройства 🔧
---------------------

### Коммутаторы 🔀

**Коммутаторы** — это специализированные сетевые устройства, предназначенные для соединения нескольких устройств с использованием Ethernet. Они являются основой современных сетей.

**Ключевые особенности:**

* 📌 Работают на **уровне 2** (канальный уровень)
* 📌 Используют **MAC-адреса** для пересылки данных
* 📌 Доступны с различным количеством портов: 4, 8, 16, 24, 32, 64 порта
* 📌 **Интеллектуальные** - отслеживают, какое устройство на каком порту

**Как работают коммутаторы:**

1. **Изучают MAC-адреса** - создают таблицу MAC-адресов
2. **Интеллектуально пересылают** - отправляют данные только на порт назначения
3. **Снижают сетевой трафик** - нет ненужных широковещательных рассылок

**Коммутаторы vs Концентраторы:**

| Характеристика         | Коммутатор                   | Концентратор                   |
| ---------------------- | ---------------------------- | ------------------------------ |
| **Интеллект**          | Умный - знает MAC-адреса     | Тупой - рассылает всё          |
| **Эффективность**      | Высокая - адресная доставка  | Низкая - заполняет все порты   |
| **Производительность** | Быстрая                      | Медленная (коллизии)           |
| **Безопасность**       | Лучше - изолированный трафик | Плохая - все видят весь трафик |
| **Стоимость**          | Выше                         | Ниже                           |
| **Уровень OSI**        | Уровень 2                    | Уровень 1                      |

**Пример:**
    Когда Устройство A отправляет данные Устройству C:
    - Концентратор: отправляет на все порты (B, C, D все получают)
    - Коммутатор: отправляет только на порт, где подключено C

**Резервирование:**

* ✅ Несколько коммутаторов могут быть соединены между собой
* ✅ Создаёт несколько путей для данных
* ✅ Если один путь выходит из строя, доступен другой
* ⚠️ Может незначительно снизить производительность из-за более длинных путей

* * *

### Маршрутизаторы 🗺️

**Маршрутизаторы** соединяют различные сети и направляют данные между ними. Они работают на **уровне 3** (сетевой уровень), используя **IP-адреса**.

**Ключевые функции:**

* 🌐 **Соединяет сети** - связывает различные LAN или подключает к Интернету
* 🗺️ **Маршрутизирует данные** - определяет лучший путь между сетями
* 🔒 **Обеспечивает безопасность** - действует как шлюз между сетями
* 📡 **NAT** - преобразует частные IP-адреса в публичные

**Процесс маршрутизации:**

1. Получает пакет с IP-адресом назначения
2. Проверяет таблицу маршрутизации для поиска лучшего пути
3. Пересылает пакет на следующий переход
4. Повторяет, пока пакет не достигнет назначения

**Маршрутизатор vs Коммутатор:**

| Характеристика       | Маршрутизатор                   | Коммутатор                        |
| -------------------- | ------------------------------- | --------------------------------- |
| **Уровень OSI**      | Уровень 3 (Сетевой)             | Уровень 2 (Канальный)             |
| **Использует**       | IP-адреса                       | MAC-адреса                        |
| **Назначение**       | Соединяет разные сети           | Соединяет устройства в одной сети |
| **Область действия** | WAN/Интернет                    | LAN                               |
| **Интеллект**        | Высокий - решения маршрутизации | Средний - изучение MAC            |

**Преимущества маршрутизации:**

* ✅ Обеспечивает связь между различными сетями
* ✅ Создаёт несколько путей для доставки данных
* ✅ Обеспечивает отказоустойчивость
* ✅ Повышает надёжность сети

* * *

Подсети (Subnetting) 🔢
-----------------------

**Подсети** — это практика разделения сети на более мелкие подсети (subnets). Это позволяет сетевым администраторам эффективно организовывать и управлять сетями.

**Зачем использовать подсети?**

* 🎯 **Эффективность** - лучшее использование пространства IP-адресов
* 🔒 **Безопасность** - изоляция различных отделов/функций
* 📊 **Управление** - проще организовать и контролировать
* ⚡ **Производительность** - снижение широковещательного трафика

**Реальный пример:** В кафе есть две отдельные сети:

1. **Сеть сотрудников** - для персонала, кассовых аппаратов, внутренних устройств
2. **Гостевая сеть** - публичный Wi-Fi для клиентов

Обе сети изолированы, но могут получать доступ к Интернету.

* * *

### Компоненты IP-адреса

**IP-адрес** состоит из **4 октетов** (32 бита), каждый в диапазоне от **0 до 255**.

**Пример:** `192.168.1.100`

**Маска подсети** также имеет 4 октета и определяет, какая часть адреса является сетевой, а какая — хостовой.

**Распространённые маски подсети:**

* `255.255.255.0` (/24) - 254 хоста
* `255.255.0.0` (/16) - 65,534 хоста
* `255.255.255.128` (/25) - 126 хостов

* * *

### Три ключевых адреса в подсетях

#### 1. Сетевой адрес 🌐

**Назначение:** Идентифицирует начало сети. Представляет саму сеть.

**Характеристики:**

* ✅ Первый адрес в подсети
* ✅ Не может быть назначен устройству
* ✅ Используется для идентификации при маршрутизации

**Пример:**

* IP устройства: `192.168.1.100`
* Сетевой адрес: `192.168.1.0`

* * *

#### 2. Адрес хоста 💻

**Назначение:** Идентифицирует отдельные устройства в подсети.

**Характеристики:**

* ✅ Уникальный адрес для каждого устройства
* ✅ Может быть любым адресом между сетевым и широковещательным
* ✅ Используется для связи устройство-устройство

**Пример:**

* Устройство 1: `192.168.1.10`
* Устройство 2: `192.168.1.25`
* Устройство 3: `192.168.1.100`

* * *

#### 3. Адрес шлюза по умолчанию 🚪

**Назначение:** Специальный адрес для устройства, которое может отправлять данные в другие сети (обычно маршрутизатор).

**Характеристики:**

* ✅ Действует как "выход" из подсети
* ✅ Обычно первый (`.1`) или последний (`.254`) адрес
* ✅ Необходим для доступа в Интернет
* ✅ Все устройства в подсети должны знать этот адрес

**Пример:**

* Сеть: `192.168.1.0/24`
* Шлюз по умолчанию: `192.168.1.1` или `192.168.1.254`
* Хосты: `192.168.1.2` до `192.168.1.253`

**Как это работает:**
    Устройство (192.168.1.100) хочет получить доступ в Интернет (8.8.8.8)
        ↓
    Отправляет пакет на шлюз по умолчанию (192.168.1.1)
        ↓
    Шлюз (маршрутизатор) пересылает в Интернет

* * *

Протокол ARP (Address Resolution Protocol) 🔍
---------------------------------------------

**ARP** — это протокол, который позволяет устройствам обнаруживать **MAC-адрес**, связанный с **IP-адресом** в локальной сети.

**Зачем нужен ARP:**

* IP-адреса (логические) используются для маршрутизации
* MAC-адреса (физические) используются для фактической доставки
* ARP преодолевает разрыв между этими двумя типами адресов

* * *

### Как работает ARP

**Кэш ARP:** Каждое устройство поддерживает **кэш ARP** - таблицу, хранящую соответствия IP-MAC.

**Пример кэша ARP:**
    IP-адрес         MAC-адрес             Возраст
    192.168.1.1      AA:BB:CC:DD:EE:FF     120с
    192.168.1.50     11:22:33:44:55:66     45с
    192.168.1.100    FF:EE:DD:CC:BB:AA     200с

* * *

### Процесс ARP: Два типа сообщений

#### 1. ARP-запрос (Broadcast) 📢

Когда устройству необходимо связаться, но оно не знает MAC-адрес:

**Процесс:**

1. Устройство A хочет отправить данные на `192.168.1.100`
2. Проверяет кэш ARP - MAC-адрес не найден
3. Отправляет **ARP-запрос** широковещательной рассылкой всей сети
4. Запрос спрашивает: "У кого IP `192.168.1.100`? Сообщите `192.168.1.50`"

**Детали ARP-запроса:**

* 📡 Отправляется на **широковещательный MAC-адрес**: `FF:FF:FF:FF:FF:FF`
* 📡 ВСЕ устройства в сети получают его
* 📡 Отвечает только целевое устройство

* * *

#### 2. ARP-ответ (Unicast) 📥

Устройство с соответствующим IP отвечает:

**Процесс:**

1. Устройство с `192.168.1.100` получает ARP-запрос
2. Распознаёт свой собственный IP-адрес
3. Отправляет **ARP-ответ** напрямую запрашивающему устройству
4. Ответ содержит: "Я `192.168.1.100`, мой MAC `AA:BB:CC:DD:EE:FF`"

**Детали ARP-ответа:**

* 📨 Отправляется напрямую (unicast) запрашивающему устройству
* 📨 Содержит MAC-адрес цели
* 📨 Запрашивающее устройство обновляет свой кэш ARP

* * *

### Полный пример ARP

    Шаг 1: Устройство A (192.168.1.50) хочет связаться с Устройством B (192.168.1.100)
    
    Шаг 2: ARP-запрос (Broadcast)
    От: 192.168.1.50 (MAC: 11:22:33:44:55:66)
    Кому: 255.255.255.255 (MAC: FF:FF:FF:FF:FF:FF)
    Сообщение: "У кого 192.168.1.100? Сообщите 192.168.1.50"
    
    Шаг 3: Все устройства получают, отвечает только 192.168.1.100
    
    Шаг 4: ARP-ответ (Unicast)
    От: 192.168.1.100 (MAC: AA:BB:CC:DD:EE:FF)
    Кому: 192.168.1.50 (MAC: 11:22:33:44:55:66)
    Сообщение: "Я 192.168.1.100, мой MAC AA:BB:CC:DD:EE:FF"
    
    Шаг 5: Устройство A обновляет кэш ARP и начинает связь

* * *

### Ключевые концепции ARP

**Помните:**

* 🔑 **MAC-адреса** = Физические идентификаторы (аппаратные)
* 🔑 **IP-адреса** = Логические идентификаторы (программные)
* 🔑 **ARP** = Преобразует IP → MAC для связи в локальной сети

**Время истечения кэша ARP:**

* Записи истекают через определённое время (обычно 2-20 минут)
* Предотвращает устаревшие записи
* Заставляет обновлять MAC-адреса

* * *

Протокол DHCP (Dynamic Host Configuration Protocol) 🔄
------------------------------------------------------

**DHCP** автоматически назначает IP-адреса устройствам в сети, устраняя необходимость в ручной настройке.

**Без DHCP:** Сетевой администратор должен вручную настраивать IP-адрес каждого устройства  
**С DHCP:** Устройства автоматически получают IP-конфигурацию при подключении

* * *

### Компоненты DHCP

**DHCP-сервер:**

* 🖥️ Управляет пулом доступных IP-адресов
* 🖥️ Назначает адреса запрашивающим устройствам
* 🖥️ Отслеживает, какие адреса используются
* 🖥️ Может быть маршрутизатором, выделенным сервером или сетевым устройством

**DHCP-клиент:**

* 💻 Любое устройство, запрашивающее IP-адрес
* 💻 Компьютеры, телефоны, принтеры, IoT-устройства

* * *

### Процесс DHCP: DORA 🎭

DHCP использует **4-шаговый процесс**, известный как **DORA**:

#### 1. **D**HCP Discover (Обнаружение) 🔍

**Клиент рассылает:** "Есть ли DHCP-сервер в этой сети?"

**Детали:**

* 📡 Широковещательное сообщение (255.255.255.255)

* 📡 У клиента ещё нет IP, использует `0.0.0.0`

* 📡 Отправляется при первом подключении устройства к сети
    Клиент: "Привет! Мне нужен IP-адрес. Есть DHCP-серверы?"
    Назначение: 255.255.255.255 (broadcast)
    Источник: 0.0.0.0 (пока нет IP)

* * *

#### 2. **O**ffer (Предложение) 🎁

**Сервер отвечает:** "Я могу предложить вам этот IP-адрес!"

**Детали:**

* 📨 DHCP-сервер отвечает с доступным IP

* 📨 Включает IP-адрес, маску подсети, шлюз, DNS

* 📨 Несколько DHCP-серверов могут ответить

* 📨 Клиент обычно принимает первое предложение
    DHCP-сервер: "Вы можете использовать 192.168.1.100!"
    Предложенный IP: 192.168.1.100
    Маска подсети: 255.255.255.0
    Шлюз: 192.168.1.1
    DNS: 8.8.8.8
    Время аренды: 24 часа

* * *

#### 3. **R**equest (Запрос) 📋

**Клиент отвечает:** "Да, я хочу этот IP-адрес!"

**Детали:**

* 📡 Клиент рассылает принятие (другие серверы должны знать)

* 📡 Формально запрашивает предложенный IP

* 📡 Отклоняет другие предложения (если несколько серверов ответили)
    Клиент: "Я принимаю предложение 192.168.1.100 от Сервера X"
    Назначение: 255.255.255.255 (broadcast)
    Запрошенный IP: 192.168.1.100

* * *

#### 4. **A**cknowledge (Подтверждение) ✅

**Сервер подтверждает:** "Подтверждено! Вы можете использовать этот IP-адрес сейчас."

**Детали:**

* ✅ Финальное подтверждение от сервера

* ✅ Предоставляет срок аренды

* ✅ Устройство теперь может использовать IP-адрес

* ✅ Коммуникация завершена
    DHCP-сервер: "Подтверждено! 192.168.1.100 ваш на 24 часа"
    Статус: ACK
    Назначенный IP: 192.168.1.100
    Действителен до: Завтра в это же время

* * *

### Диаграмма DHCP DORA

    Клиент                                  DHCP-сервер
      |                                          |
      |------ 1. DHCP Discover (Broadcast) ---->| "У кого-нибудь есть IP для меня?"
      |                                          |
      |<----- 2. DHCP Offer -------------------|  "Вот 192.168.1.100"
      |                                          |
      |------ 3. DHCP Request (Broadcast) ----->| "Я возьму этот IP!"
      |                                          |
      |<----- 4. DHCP ACK ---------------------|  "Подтверждено!"
      |                                          |
      [Устройство теперь имеет IP: 192.168.1.100]

* * *

### Информация об аренде DHCP

**Что получает клиент:**

* 📍 **IP-адрес** - уникальный адрес для устройства
* 📍 **Маска подсети** - определяет размер сети
* 📍 **Шлюз по умолчанию** - IP маршрутизатора для доступа в Интернет
* 📍 **DNS-серверы** - для разрешения доменных имён
* 📍 **Время аренды** - как долго IP действителен

**Типичные сроки аренды:**

* Домашние сети: 24 часа до 7 дней
* Корпоративные сети: 8 часов до 24 часов
* Публичный Wi-Fi: 30 минут до 2 часов

* * *

### Продление аренды DHCP

**Процесс:**

1. Клиент использует IP в течение срока аренды
2. При достижении 50% времени аренды клиент пытается продлить
3. Если продление не удаётся, пытается снова при 87.5% срока
4. Если всё ещё не удаётся, должен начать процесс DORA снова

**Пример:**

* Срок аренды: 24 часа
* Попытка продления 1: Через 12 часов (50%)
* Попытка продления 2: Через 21 час (87.5%)
* Если обе не удались: Начать DORA снова через 24 часа

* * *

### Преимущества и недостатки DHCP

**Преимущества:**

* ✅ **Автоматическая настройка** - нет ручной установки
* ✅ **Централизованное управление** - легко управлять IP-адресами
* ✅ **Предотвращает конфликты** - нет дублирующихся IP
* ✅ **Эффективное использование** пространства IP-адресов
* ✅ **Легко масштабировать** - добавляйте устройства без перенастройки

**Недостатки:**

* ❌ **Единая точка отказа** - если DHCP-сервер упал, новые устройства не могут подключиться
* ❌ **Сетевой трафик** - сообщения DHCP используют пропускную способность
* ❌ **Проблемы безопасности** - возможны мошеннические DHCP-серверы
* ❌ **Изменяющиеся IP-адреса** - могут усложнить некоторые приложения

* * *

### Статическое vs Динамическое назначение IP

| Характеристика   | Статический IP                          | Динамический IP (DHCP)               |
| ---------------- | --------------------------------------- | ------------------------------------ |
| **Настройка**    | Ручная                                  | Автоматическая                       |
| **Управление**   | Сложное (большие сети)                  | Простое                              |
| **Конфликты IP** | Возможны                                | Предотвращены                        |
| **Идеален для**  | Серверы, принтеры, сетевое оборудование | Конечные пользовательские устройства |
| **Надёжность**   | Высокая (не меняется)                   | Средняя (может меняться)             |
| **Гибкость**     | Низкая                                  | Высокая                              |

**Когда использовать статический:**

* 🖥️ Серверы
* 🖨️ Принтеры
* 🔧 Сетевое оборудование (коммутаторы, маршрутизаторы)
* 📹 IP-камеры
* 🎮 Игровые консоли (проброс портов)

**Когда использовать DHCP:**

* 💻 Ноутбуки
* 📱 Смартфоны
* 🖥️ Настольные компьютеры
* 📺 Умные телевизоры
* 🏠 IoT-устройства

* * *

Практические команды для сетевого администрирования 💻
------------------------------------------------------

### Просмотр IP, назначенного DHCP (Windows):

    ipconfig /all

### Просмотр IP, назначенного DHCP (Linux/Mac):

    ifconfig
    # или
    ip addr show

### Продление аренды DHCP (Windows):

    ipconfig /release
    ipconfig /renew

### Продление аренды DHCP (Linux):

    sudo dhclient -r  # освободить
    sudo dhclient     # продлить

### Просмотр кэша ARP (Windows/Linux/Mac):

    arp -a

### Очистка кэша ARP (Windows):

    arp -d

### Очистка кэша ARP (Linux):

    sudo ip -s -s neigh flush all

### Добавление статической записи ARP:

    # Windows
    arp -s 192.168.1.100 AA-BB-CC-DD-EE-FF
    
    # Linux
    sudo arp -s 192.168.1.100 AA:BB:CC:DD:EE:FF

* * *

Лучшие практики сетевых топологий 📋
------------------------------------

### Выбор правильной топологии:

**Звездообразная топология** - Выбирайте когда:

* ✅ Бюджет позволяет качественное оборудование
* ✅ Надёжность критична
* ✅ Сеть будет расти со временем
* ✅ Производительность важна

**Шинная топология** - Выбирайте когда:

* ✅ Временная или тестовая сеть
* ✅ Очень ограниченный бюджет
* ✅ Малое количество устройств (< 5)
* ⚠️ Не рекомендуется для продакшена

**Кольцевая топология** - Выбирайте когда:

* ✅ Требуется устаревшая система
* ✅ Сеть Token Ring
* ✅ Справедливый доступ — приоритет
* ⚠️ Редко используется в современных сетях

* * *

Устранение сетевых проблем 🔧
-----------------------------

### Общие шаги диагностики:

1. **Проверка физических соединений**
   
   * Подключены ли кабели?
   * Горят ли индикаторы линка?
   * Попробуйте другой кабель/порт

2. **Проверка IP-конфигурации**
      ipconfig /all  # Windows
      ip addr show   # Linux

3. **Проверка DHCP**
   
   * Работает ли DHCP-сервер?
   * Есть ли доступные адреса?
   * Попробуйте ручное назначение IP

4. **Тест локальной связности**
      ping 192.168.1.1  # Шлюз

5. **Проверка ARP**
      arp -a  # Просмотр кэша ARP

6. **Тест внешней связности**
      ping 8.8.8.8  # Google DNS

7. **Проверка DNS**
      nslookup google.com
   
   

* * *

Вопросы безопасности 🔒
-----------------------

### Проблемы безопасности ARP:

**ARP Spoofing атака:**

* 🔴 Атакующий отправляет поддельные ARP-ответы
* 🔴 Перенаправляет трафик через машину атакующего
* 🔴 Возможна атака "человек посередине"

**Защита:**

* 🛡️ Используйте **Dynamic ARP Inspection (DAI)** на коммутаторах
* 🛡️ Статические ARP-записи для критических устройств
* 🛡️ Средства мониторинга сети

### Проблемы безопасности DHCP:

**Мошеннический DHCP-сервер:**

* 🔴 Неавторизованный DHCP-сервер в сети
* 🔴 Может назначить вредоносный шлюз/DNS
* 🔴 Перехват или перенаправление трафика

**Защита:**

* 🛡️ **DHCP Snooping** на коммутаторах
* 🛡️ Только авторизованные DHCP-серверы
* 🛡️ Безопасность портов

**DHCP Starvation атака:**

* 🔴 Атакующий запрашивает все доступные IP
* 🔴 Легитимные пользователи не могут получить адреса
* 🔴 Отказ в обслуживании

**Защита:**

* 🛡️ Ограничение скорости DHCP-запросов
* 🛡️ Достаточный пул IP-адресов
* 🛡️ Мониторинг логов DHCP

* * *

Краткое резюме: Ключевые концепции 🎯
-------------------------------------

### Сетевые топологии:

1. **Звезда** ⭐ - Самая распространённая, надёжная, дорогая
2. **Шина** 🚌 - Устаревшая, дешёвая, ненадёжная
3. **Кольцо** 🔄 - Устаревшая, справедливый доступ, единая точка отказа

### Сетевые устройства:

1. **Коммутаторы** 🔀 - Соединяют устройства в одной сети (Уровень 2)
2. **Маршрутизаторы** 🗺️ - Соединяют разные сети (Уровень 3)

### IP-конфигурация:

1. **Сетевой адрес** 🌐 - Идентифицирует сеть
2. **Адрес хоста** 💻 - Идентифицирует отдельные устройства
3. **Шлюз по умолчанию** 🚪 - Выход в другие сети

### Протоколы:

1. **ARP** 🔍 - Преобразует IP-адреса в MAC-адреса
2. **DHCP** 🔄 - Автоматически назначает IP-адреса (процесс DORA)

### Помните:

* 🔑 **MAC = Физический**, **IP = Логический**

* 🔑 **ARP = Локальная сеть**

* 🔑 **DHCP = Автоматическая** IP-конфигурация

* 🔑 **Шлюз = Выход** в другие сети
