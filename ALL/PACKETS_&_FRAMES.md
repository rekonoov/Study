Packets, Frames, TCP/UDP - Complete Guide 📦
============================================

> **English** 🇬🇧 and **Russian** 🇷🇺 versions included

* * *

English Version 🇬🇧
====================

* * *

What are Packets and Frames? 🤔
-------------------------------

**Packets** and **frames** are small fragments of data that, when combined, form a larger piece of information or message. However, in the OSI model, these are two different things.

### Key Difference:

| Term       | OSI Layer           | Contains               | Analogy                    |
| ---------- | ------------------- | ---------------------- | -------------------------- |
| **Packet** | Layer 3 (Network)   | IP header + payload    | Letter inside envelope     |
| **Frame**  | Layer 2 (Data Link) | MAC addresses + packet | Envelope containing letter |

**Packet** — a fragment of data from **Layer 3 (Network Layer)** containing IP header and payload.

**Frame** — used at **Layer 2 (Data Link Layer)**, which encapsulates the packet and adds additional information such as MAC addresses.

* * *

Postal Mail Analogy 📬
----------------------

Think of sending a letter by mail:

| Component              | Network Equivalent |
| ---------------------- | ------------------ |
| **Letter content**     | Data/Payload       |
| **Letter in envelope** | Packet (Layer 3)   |
| **Addressed envelope** | Frame (Layer 2)    |
| **Street address**     | IP address         |
| **House number**       | MAC address        |

**Process:**

1. Write letter (create data)
2. Put in envelope (create packet with IP addresses)
3. Write address on envelope (create frame with MAC addresses)
4. Mail carrier delivers (physical transmission)

**At destination:**

1. Receive envelope (receive frame)
2. Open envelope (decapsulation - remove frame)
3. Read letter (extract packet and data)

This process is called **encapsulation**. When we talk about anything related to IP addresses, we're referring to packets. When the encapsulating information is removed, we're dealing with the frame itself.

* * *

Why Use Packets? 🎯
-------------------

Packets are an efficient way to communicate data across networked devices. Since data is exchanged in small pieces, there's less chance of bottlenecking on the network than if large messages were sent all at once.

### Example: Loading an Image

When you download an image from a website, the image isn't sent to your computer as one whole piece. Instead, it's sent in small chunks (packets) that are then recreated on your computer.
    Original Image (1MB)
             ↓
    Split into packets
             ↓
    ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐
    │Pkt 1│ │Pkt 2│ │Pkt 3│ │Pkt 4│
    └─────┘ └─────┘ └─────┘ └─────┘
             ↓
    Sent over network (may take different routes)
             ↓
    ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐
    │Pkt 1│ │Pkt 3│ │Pkt 2│ │Pkt 4│ (arrive in different order)
    └─────┘ └─────┘ └─────┘ └─────┘
             ↓
    Reassembled on your computer
             ↓
    Complete Image (1MB)

**Benefits:**

* ✅ No network bottlenecks
* ✅ Multiple packets travel simultaneously
* ✅ If one packet is lost, only that packet needs retransmission
* ✅ Better bandwidth utilization

* * *

Packet Structure 🏗️
--------------------

Packets have different structures depending on the type of packet being sent. Networks are full of standards and protocols that act as a set of rules for how packets are handled on a device.

### IP Packet Headers:

Important headers in an IP packet:

| Header                 | Description           | Example             |
| ---------------------- | --------------------- | ------------------- |
| **Source IP**          | Sender's IP address   | 192.168.1.100       |
| **Destination IP**     | Receiver's IP address | 8.8.8.8             |
| **Time To Live (TTL)** | Max number of hops    | 64                  |
| **Protocol**           | Upper layer protocol  | TCP (6) or UDP (17) |
| **Checksum**           | Error checking        | 0x4A3B              |

* * *

TCP/IP Protocol 🤝
------------------

**TCP (Transmission Control Protocol)** is another one of the rules used in networking.

This protocol is very similar to the OSI model. The TCP/IP protocol consists of four layers and is essentially a summarized version of the OSI model:

### TCP/IP Model (4 Layers):

    ┌─────────────────────┐
    │  Application Layer  │ ← HTTP, FTP, SMTP
    ├─────────────────────┤
    │  Transport Layer    │ ← TCP, UDP
    ├─────────────────────┤
    │  Internet Layer     │ ← IP, ICMP
    ├─────────────────────┤
    │ Network Interface   │ ← Ethernet, Wi-Fi
    └─────────────────────┘

Just like the OSI model, information is added to each layer of the TCP model as a piece of data (or packet) passes through it. This process is called **encapsulation**, and the reverse is **decapsulation**.

* * *

TCP Characteristics 🔒
----------------------

One defining feature of TCP is that it is **connection-based**, meaning TCP must establish a connection between the client and a device acting as a server before data is sent.

Because of this, TCP guarantees that any data sent will be received on the other end. This process is called the **three-way handshake**.

### TCP Advantages and Disadvantages:

| Advantages ✅             | Disadvantages ❌              |
| ------------------------ | ---------------------------- |
| Guarantees data accuracy | Requires reliable connection |
| Synchronizes devices     | Slower than UDP              |
| Error checking           | More overhead                |
| Ordered delivery         | Can create bottlenecks       |
| Flow control             | Requires more resources      |

### When to Use TCP:

* ✅ File transfer (FTP)
* ✅ Web browsing (HTTP/HTTPS)
* ✅ Email (SMTP, IMAP)
* ✅ Any application requiring complete data

* * *

TCP Packet Headers 📋
---------------------

TCP packets contain various sections of information called **headers** that are added during encapsulation.

### Important TCP Headers:

| Header                    | Description                               |
| ------------------------- | ----------------------------------------- |
| **Source Port**           | Port number of sender (e.g., 80 for HTTP) |
| **Destination Port**      | Port number of receiver                   |
| **Sequence Number**       | Order of packet in data stream            |
| **Acknowledgment Number** | Next expected sequence number             |
| **Checksum**              | Error checking for data integrity         |
| **Flags**                 | Control flags (SYN, ACK, FIN, RST, etc.)  |
| **Window Size**           | Amount of data receiver can accept        |

* * *

TCP Three-Way Handshake 🤝
--------------------------

The **Three-Way Handshake** is the term given to the process used to establish a connection between two devices using TCP.

### Special Messages:

| Message     | Full Name                  | Description                                      |
| ----------- | -------------------------- | ------------------------------------------------ |
| **SYN**     | Synchronize                | Initiates connection, proposes sequence number   |
| **SYN/ACK** | Synchronize Acknowledgment | Accepts connection, proposes own sequence number |
| **ACK**     | Acknowledgment             | Confirms receipt, connection established         |
| **FIN**     | Finish                     | Closes connection                                |
| **RST**     | Reset                      | Aborts connection                                |

### Three-Way Handshake Process:

    Client (Alice)                    Server (Bob)
          |                                |
          |--------> SYN (seq=0) --------->|  Step 1: Client requests connection
          |                                |  "Here's my ISN for synchronization"
          |                                |
          |<----- SYN/ACK (seq=5000) <-----|  Step 2: Server acknowledges
          |        ack=1                   |  "Here's my ISN, I acknowledge yours"
          |                                |
          |-------> ACK (seq=1) ---------->|  Step 3: Client acknowledges
          |        ack=5001                |  "I acknowledge your ISN, here's data"
          |                                |
          |    CONNECTION ESTABLISHED      |
          |                                |
          |<======= DATA TRANSFER ========>|

Any data sent is given a random number sequence and is reconstructed using this number sequence and incrementing by 1. Both computers must agree on the same number sequence for data to be sent in the correct order.

**Step 1 - SYN:** Client says "Here is my Initial Sequence Number (ISN) to SYNchronize with (0)"

**Step 2 - SYN/ACK:** Server says "Here is my Initial Sequence Number (ISN) to SYNchronize with (5000), and I ACKnowledge your initial number sequence (0)"

**Step 3 - ACK:** Client says "I ACKnowledge your Initial Sequence Number (ISN) of (5000), here is some data that is my ISN+1 (0 + 1)"

* * *

TCP Connection Termination 👋
-----------------------------

Let's briefly explain the process of closing a TCP connection. First, TCP will close a connection once a device has determined that the other device has successfully received all of the data.

To initiate the closure of a TCP connection, a device will send a **"FIN"** packet to the other device. Of course, with TCP, the other device must acknowledge this packet with an **ACK**.

### TCP Closing Process:

    Client (Alice)                    Server (Bob)
          |                                |
          |--------> FIN (seq=100) ------->|  Step 1: Alice wants to close
          |                                |  "I'm done sending data"
          |                                |
          |<------- ACK (ack=101) <--------|  Step 2: Bob acknowledges
          |                                |  "I got your FIN"
          |                                |
          |<------ FIN (seq=300) <---------|  Step 3: Bob also closes
          |                                |  "I'm done too"
          |                                |
          |-------> ACK (ack=301) -------->|  Step 4: Alice acknowledges
          |                                |  "Got it, goodbye!"
          |                                |
          |   CONNECTION CLOSED            |

In the illustration, we can see that Alice has sent Bob a **"FIN"** packet. Because Bob received this, he will let Alice know that he received it and that he also wants to close the connection (using FIN). Alice has heard Bob loud and clear and will let Bob know that she acknowledges this.

* * *

UDP Protocol ⚡
--------------

**UDP (User Datagram Protocol)** is another protocol used to communicate data between devices.

Unlike its brother TCP, UDP is a **stateless** protocol that doesn't require a constant connection between the two devices for data to be sent. For example, the three-way handshake does not occur, nor is there any synchronization between the two devices.

### UDP vs TCP:

| TCP                       | UDP                         |
| ------------------------- | --------------------------- |
| Connection-oriented       | Connectionless              |
| Reliable                  | Unreliable                  |
| Ordered delivery          | No ordering                 |
| Error checking & recovery | Minimal error checking      |
| Slow                      | Fast                        |
| Heavy (20+ byte header)   | Lightweight (8 byte header) |

Recall some of the comparisons made about these two protocols in Room 3: "OSI Model". Namely, UDP is used in situations where applications can tolerate data loss (such as video streaming or voice chat) or in scenarios where an unstable connection is not necessarily critical.

### UDP Advantages and Disadvantages:

| Advantages ✅                  | Disadvantages ❌                 |
| ----------------------------- | ------------------------------- |
| Much faster than TCP          | No guarantee of delivery        |
| Lower latency                 | No error recovery               |
| Less bandwidth overhead       | Packets may arrive out of order |
| Good for unstable connections | Not suitable for critical data  |
| No connection state           | Application must handle errors  |

### When to Use UDP:

* ✅ Video streaming (YouTube, Netflix)
* ✅ Online gaming
* ✅ Voice calls (VoIP, Zoom)
* ✅ Live broadcasts
* ✅ DNS queries
* ✅ DHCP

* * *

UDP Packet Structure 📦
-----------------------

UDP packets are **much simpler** than TCP packets and have fewer headers.

### UDP Headers:

| Header               | Description                       | Size    |
| -------------------- | --------------------------------- | ------- |
| **Source Port**      | Sender's port number              | 16 bits |
| **Destination Port** | Receiver's port number            | 16 bits |
| **Length**           | Total length of UDP packet        | 16 bits |
| **Checksum**         | Error checking (optional in IPv4) | 16 bits |

**Total Header: Only 8 bytes!** (TCP has 20+ bytes)

* * *

UDP Communication 📡
--------------------

As mentioned, no process takes place in setting up a connection between two devices. This means that there is no regard for whether data is received, and there are no safeguards such as those offered by TCP, such as data integrity.

**UDP is a stateless protocol** - no acknowledgments are sent during a connection.

### UDP Communication Process:

    Client (Alice)                    Server (Bob)
          |                                |
          |--------> DATA (packet 1) ----->|  Just send data
          |                                |  No SYN, no handshake
          |--------> DATA (packet 2) ----->|  
          |                                |  May arrive
          |--------> DATA (packet 3) ----->|  
          |                                |  May be lost
          |--------> DATA (packet 4) ----->|  
          |                                |  May arrive out of order
          |                                |
          |  No acknowledgments!           |

The diagram below shows a normal UDP connection between Alice and Bob. In real life, this is a connection between two devices - with no acknowledgments being sent.

* * *

TCP vs UDP: Complete Comparison 🆚
----------------------------------

### Visual Comparison:

    TCP - Reliable but Slow:
    ┌──────┐     ┌──────┐     ┌──────┐
    │ SYN  │────▶│Server│────▶│SYN/  │  Setup connection
    └──────┘     └──────┘     │ ACK  │  (overhead)
                              └──────┘
                                  │
                                  ▼
    ┌──────┐     ┌──────┐     ┌──────┐
    │Data 1│────▶│Server│────▶│ ACK  │  Send + Acknowledge
    └──────┘     └──────┘     └──────┘  (slow but reliable)
    
    
    UDP - Fast but Unreliable:
    ┌──────┐     ┌──────┐
    │Data 1│────▶│Server│  No handshake
    └──────┘     └──────┘  (fast!)
    ┌──────┐     ┌──────┐
    │Data 2│────▶│ ❌   │  Might be lost
    └──────┘     └──────┘  (but who cares, send next!)

* * *

Summary: Quick Reference 📋
---------------------------

### Packets vs Frames:

    Frame (Layer 2)
      ├── MAC Source
      ├── MAC Destination
      └── Packet (Layer 3)
            ├── IP Source
            ├── IP Destination
            └── Data

### TCP vs UDP:

    TCP = Reliable Phone Call
    - Establish connection
    - Confirm everything
    - Hang up properly
    
    UDP = Shouting Across Room
    - Just yell
    - Hope they hear
    - Move on

### When to Use:

    Use TCP when:
    ✅ Data must arrive completely
    ✅ Order matters
    ✅ Examples: Files, email, web pages
    
    Use UDP when:
    ✅ Speed > accuracy
    ✅ Real-time matters
    ✅ Examples: Streaming, games, calls

* * *

Русская версия 🇷🇺
===================

* * *

Что такое пакеты и кадры? 🤔
----------------------------

**Пакеты** и **кадры** — это небольшие фрагменты данных, которые, объединяясь, образуют более крупный фрагмент информации или сообщение. Однако в модели OSI это две разные вещи.

### Ключевое различие:

| Термин    | Уровень OSI           | Содержит              | Аналогия               |
| --------- | --------------------- | --------------------- | ---------------------- |
| **Пакет** | Уровень 3 (Сетевой)   | IP-заголовок + данные | Письмо внутри конверта |
| **Кадр**  | Уровень 2 (Канальный) | MAC-адреса + пакет    | Конверт с письмом      |

**Пакет** — это фрагмент данных **уровня 3 (сетевого уровня)** модели OSI, содержащий такую информацию, как IP-заголовок и полезную нагрузку.

**Кадр**, однако, используется на **уровне 2 (уровне канала передачи данных)** модели OSI, который инкапсулирует пакет и добавляет дополнительную информацию, такую как MAC-адреса.

* * *

Аналогия с почтой 📬
--------------------

Этот процесс можно сравнить с отправкой письма по почте:

| Компонент             | Сетевой эквивалент       |
| --------------------- | ------------------------ |
| **Содержимое письма** | Данные/Полезная нагрузка |
| **Письмо в конверте** | Пакет (Уровень 3)        |
| **Конверт с адресом** | Кадр (Уровень 2)         |
| **Адрес улицы**       | IP-адрес                 |
| **Номер дома**        | MAC-адрес                |

**Процесс:**

1. Написать письмо (создать данные)
2. Положить в конверт (создать пакет с IP-адресами)
3. Написать адрес на конверте (создать кадр с MAC-адресами)
4. Почтальон доставляет (физическая передача)

**В пункте назначения:**

1. Получить конверт (получить кадр)
2. Открыть конверт (декапсуляция - удалить кадр)
3. Прочитать письмо (извлечь пакет и данные)

Конверт — это кадр, который используется для перемещения содержимого (в этой аналогии — пакета) конверта в другое место. Как только получатель откроет конверт (кадр), он будет знать, как переслать само письмо (пакет).

Этот процесс называется **инкапсуляцией**. Когда мы говорим о чём-либо, связанном с IP-адресами, мы имеем в виду пакеты. Когда инкапсулирующая информация удаляется, мы говорим о самом кадре.

* * *

Зачем использовать пакеты? 🎯
-----------------------------

Пакеты — это эффективный способ передачи данных между сетевыми устройствами. Поскольку эти данные обмениваются небольшими частями, вероятность возникновения узких мест в сети меньше, чем при одновременной отправке больших сообщений.

### Пример: Загрузка изображения

При загрузке изображения с веб-сайта это изображение не отправляется на ваш компьютер целиком, а по частям, которые затем воссоздаются на вашем компьютере.
    Оригинальное изображение (1MB)
             ↓
    Разделяется на пакеты
             ↓
    ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐
    │Пакет│ │Пакет│ │Пакет│ │Пакет│
    │  1  │ │  2  │ │  3  │ │  4  │
    └─────┘ └─────┘ └─────┘ └─────┘
             ↓
    Отправка по сети (могут идти разными путями)
             ↓
    ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐
    │Пакет│ │Пакет│ │Пакет│ │Пакет│
    │  1  │ │  3  │ │  2  │ │  4  │ (приходят в разном порядке)
    └─────┘ └─────┘ └─────┘ └─────┘
             ↓
    Собирается на вашем компьютере
             ↓
    Полное изображение (1MB)

Изображение кошки разделено на три пакета, которые воссоздаются при поступлении на компьютер, образуя окончательное изображение.

**Преимущества:**

* ✅ Нет узких мест в сети
* ✅ Несколько пакетов передаются одновременно
* ✅ Если один пакет потерян, нужно переслать только его
* ✅ Лучшее использование пропускной способности

* * *

Структура пакета 🏗️
--------------------

Пакеты имеют разную структуру в зависимости от типа отправляемого пакета. Сети полны стандартов и протоколов, которые действуют как набор правил обработки пакетов на устройстве.

### Заголовки IP-пакета:

Важные заголовки в IP-пакете:

| Заголовок              | Описание                 | Пример               |
| ---------------------- | ------------------------ | -------------------- |
| **IP источника**       | IP-адрес отправителя     | 192.168.1.100        |
| **IP назначения**      | IP-адрес получателя      | 8.8.8.8              |
| **Time To Live (TTL)** | Макс. число переходов    | 64                   |
| **Протокол**           | Протокол верхнего уровня | TCP (6) или UDP (17) |
| **Контрольная сумма**  | Проверка ошибок          | 0x4A3B               |

* * *

Протокол TCP/IP 🤝
------------------

**TCP (Transmission Control Protocol или сокращенно Протокол управления передачей)** — ещё одно из правил, используемых в сетях.

Этот протокол очень похож на модель OSI. Протокол TCP/IP состоит из четырёх уровней и, по сути, является сокращённой версией модели OSI:

### Модель TCP/IP (4 уровня):

    ┌─────────────────────┐
    │  Прикладной уровень │ ← HTTP, FTP, SMTP
    ├─────────────────────┤
    │ Транспортный уровень│ ← TCP, UDP
    ├─────────────────────┤
    │   Интернет-уровень  │ ← IP, ICMP
    ├─────────────────────┤
    │ Уровень сетевого    │ ← Ethernet, Wi-Fi
    │    интерфейса       │
    └─────────────────────┘

Очень похоже на то, как работает модель OSI, информация добавляется к каждому уровню модели TCP по мере прохождения фрагмента данных (или пакета) через него. Этот процесс называется **инкапсуляцией**, а его обратный процесс — **декапсуляцией**.

* * *

Характеристики TCP 🔒
---------------------

Одной из отличительных черт TCP является то, что он **основан на соединении**, что означает, что TCP должен установить соединение между клиентом и устройством, действующим в качестве сервера, перед отправкой данных.

Благодаря этому TCP **гарантирует**, что любые отправленные данные будут получены на другом конце. Этот процесс называется **трёхсторонним рукопожатием**.

### Преимущества и недостатки TCP:

| Преимущества ✅              | Недостатки ❌                |
| --------------------------- | --------------------------- |
| Гарантирует точность данных | Требует надёжное соединение |
| Синхронизирует устройства   | Медленнее UDP               |
| Проверка ошибок             | Больше накладных расходов   |
| Упорядоченная доставка      | Может создавать узкие места |
| Управление потоком          | Требует больше ресурсов     |

### Когда использовать TCP:

* ✅ Передача файлов (FTP)
* ✅ Веб-браузинг (HTTP/HTTPS)
* ✅ Электронная почта (SMTP, IMAP)
* ✅ Любое приложение, требующее полных данных

* * *

Заголовки TCP-пакета 📋
-----------------------

Пакеты TCP содержат различные разделы информации, известные как **заголовки**, которые добавляются при инкапсуляции.

### Важные TCP-заголовки:

| Заголовок               | Описание                                            |
| ----------------------- | --------------------------------------------------- |
| **Порт источника**      | Номер порта отправителя (например, 80 для HTTP)     |
| **Порт назначения**     | Номер порта получателя                              |
| **Порядковый номер**    | Порядок пакета в потоке данных                      |
| **Номер подтверждения** | Следующий ожидаемый порядковый номер                |
| **Контрольная сумма**   | Проверка ошибок для целостности данных              |
| **Флаги**               | Управляющие флаги (SYN, ACK, FIN, RST и т.д.)       |
| **Размер окна**         | Количество данных, которое получатель может принять |

* * *

Трёхстороннее рукопожатие TCP 🤝
--------------------------------

**Трёхстороннее рукопожатие** — термин, обозначающий процесс установления соединения между двумя устройствами с использованием TCP.

### Специальные сообщения:

| Сообщение   | Полное название            | Описание                                               |
| ----------- | -------------------------- | ------------------------------------------------------ |
| **SYN**     | Synchronize                | Инициирует соединение, предлагает порядковый номер     |
| **SYN/ACK** | Synchronize Acknowledgment | Принимает соединение, предлагает свой порядковый номер |
| **ACK**     | Acknowledgment             | Подтверждает получение, соединение установлено         |
| **FIN**     | Finish                     | Закрывает соединение                                   |
| **RST**     | Reset                      | Прерывает соединение                                   |

### Процесс трёхстороннего рукопожатия:

    Клиент (Алиса)                    Сервер (Боб)
          |                                |
          |--------> SYN (seq=0) --------->|  Шаг 1: Клиент запрашивает соединение
          |                                |  "Вот мой ISN для синхронизации"
          |                                |
          |<----- SYN/ACK (seq=5000) <-----|  Шаг 2: Сервер подтверждает
          |        ack=1                   |  "Вот мой ISN, я подтверждаю твой"
          |                                |
          |-------> ACK (seq=1) ---------->|  Шаг 3: Клиент подтверждает
          |        ack=5001                |  "Подтверждаю твой ISN, вот данные"
          |                                |
          |   СОЕДИНЕНИЕ УСТАНОВЛЕНО       |
          |                                |
          |<======= ПЕРЕДАЧА ДАННЫХ ======>|

Трёхстороннее рукопожатие осуществляется с помощью нескольких специальных сообщений.

Любые отправленные данные получают случайную последовательность чисел и восстанавливаются с использованием этой последовательности чисел и приращением на 1. Оба компьютера должны согласовать одну и ту же последовательность чисел, чтобы данные отправлялись в правильном порядке. Этот порядок согласовывается в три этапа:

**Шаг 1 - SYN:** Клиент говорит "Вот мой начальный номер последовательности (ISN) для синхронизации с SYN (0)"

**Шаг 2 - SYN/ACK:** Сервер говорит "Вот мой начальный порядковый номер (ISN) для SYNхронизации (5000), и я подтверждаю твою начальную последовательность чисел (0)"

**Шаг 3 - ACK:** Клиент говорит "Я подтверждаю твой начальный порядковый номер (ISN) (5000), вот некоторые данные, которые являются моим ISN+1 (0 + 1)"

* * *

Завершение соединения TCP 👋
----------------------------

Давайте кратко объясним процесс закрытия соединения TCP. Во-первых, TCP закроет соединение, как только одно устройство определит, что другое устройство успешно получило все данные.

Чтобы инициировать закрытие соединения TCP, устройство отправляет пакет **"FIN"** другому устройству. Конечно, при использовании TCP другое устройство также должно подтвердить получение этого пакета с помощью **ACK**.

### Процесс закрытия TCP:

    Клиент (Алиса)                    Сервер (Боб)
          |                                |
          |--------> FIN (seq=100) ------->|  Шаг 1: Алиса хочет закрыть
          |                                |  "Я закончила отправку данных"
          |                                |
          |<------- ACK (ack=101) <--------|  Шаг 2: Боб подтверждает
          |                                |  "Я получил твой FIN"
          |                                |
          |<------ FIN (seq=300) <---------|  Шаг 3: Боб тоже закрывает
          |                                |  "Я тоже закончил"
          |                                |
          |-------> ACK (ack=301) -------->|  Шаг 4: Алиса подтверждает
          |                                |  "Понял, до свидания!"
          |                                |
          |   СОЕДИНЕНИЕ ЗАКРЫТО           |

На иллюстрации мы видим, что Алиса отправила Бобу пакет **"FIN"**. Поскольку Боб получил его, он сообщит Алисе, что он его получил и что он также хочет закрыть соединение (используя FIN). Алиса ясно услышала Боба и сообщит ему, что она подтверждает это.

* * *

Протокол UDP ⚡
--------------

**Протокол UDP (User Datagram Protocol)** — ещё один протокол, используемый для обмена данными между устройствами.

В отличие от своего «брата» TCP, UDP является протоколом **без состояния**, который не требует постоянного соединения между двумя устройствами для отправки данных. Например, трёхстороннее рукопожатие не происходит, и между двумя устройствами нет никакой синхронизации.

### UDP vs TCP:

| TCP                              | UDP                         |
| -------------------------------- | --------------------------- |
| С установлением соединения       | Без установления соединения |
| Надёжный                         | Ненадёжный                  |
| Упорядоченная доставка           | Без упорядочивания          |
| Проверка ошибок и восстановление | Минимальная проверка ошибок |
| Медленный                        | Быстрый                     |
| Тяжёлый (20+ байт заголовок)     | Лёгкий (8 байт заголовок)   |

UDP используется в ситуациях, когда приложения могут допустить потерю данных (например, при потоковой передаче видео или голосовом чате), или в сценариях, когда нестабильное соединение не является критическим.

### Преимущества и недостатки UDP:

| Преимущества ✅                       | Недостатки ❌                          |
| ------------------------------------ | ------------------------------------- |
| Намного быстрее TCP                  | Нет гарантии доставки                 |
| Меньшая задержка                     | Нет восстановления ошибок             |
| Меньше использует полосу пропускания | Пакеты могут прийти не по порядку     |
| Хорош для нестабильных соединений    | Не подходит для критичных данных      |
| Нет состояния соединения             | Приложение должно обрабатывать ошибки |

### Когда использовать UDP:

* ✅ Потоковое видео (YouTube, Netflix)
* ✅ Онлайн-игры
* ✅ Голосовые звонки (VoIP, Zoom)
* ✅ Прямые трансляции
* ✅ DNS-запросы
* ✅ DHCP

* * *

Структура UDP-пакета 📦
-----------------------

Пакеты UDP **гораздо проще**, чем пакеты TCP, и имеют меньше заголовков.

### Заголовки UDP:

| Заголовок             | Описание                             | Размер |
| --------------------- | ------------------------------------ | ------ |
| **Порт источника**    | Номер порта отправителя              | 16 бит |
| **Порт назначения**   | Номер порта получателя               | 16 бит |
| **Длина**             | Общая длина UDP-пакета               | 16 бит |
| **Контрольная сумма** | Проверка ошибок (опциональна в IPv4) | 16 бит |

**Общий заголовок: Всего 8 байт!** (TCP имеет 20+ байт)

Однако оба протокола имеют некоторые стандартные заголовки.

* * *

Коммуникация UDP 📡
-------------------

Как уже упоминалось, при установке соединения между двумя устройствами не происходит никаких процессов. Это означает, что не учитывается, получены ли данные, и нет таких мер безопасности, как те, которые предлагает TCP, например, целостность данных.

**UDP является безсостоятельным протоколом** - во время соединения не отправляется никаких подтверждений.

### Процесс коммуникации UDP:

    Клиент (Алиса)                    Сервер (Боб)
          |                                |
          |--------> ДАННЫЕ (пакет 1) ---->|  Просто отправить данные
          |                                |  Нет SYN, нет рукопожатия
          |--------> ДАННЫЕ (пакет 2) ---->|  
          |                                |  Может прийти
          |--------> ДАННЫЕ (пакет 3) ---->|  
          |                                |  Может быть потерян
          |--------> ДАННЫЕ (пакет 4) ---->|  
          |                                |  Может прийти не по порядку
          |                                |
          |  Нет подтверждений!            |

На схеме показано обычное соединение UDP между Алисой и Бобом. В реальной жизни это соединение между двумя устройствами - без отправки подтверждений.

* * *

TCP vs UDP: Полное сравнение 🆚
-------------------------------

### Визуальное сравнение:

    TCP - Надёжный, но медленный:
    ┌──────┐     ┌──────┐     ┌──────┐
    │ SYN  │────▶│Сервер│────▶│SYN/  │  Установка соединения
    └──────┘     └──────┘     │ ACK  │  (накладные расходы)
                              └──────┘
                                  │
                                  ▼
    ┌──────┐     ┌──────┐     ┌──────┐
    │Данные│────▶│Сервер│────▶│ ACK  │  Отправка + Подтверждение
    │  1   │     └──────┘     └──────┘  (медленно, но надёжно)
    └──────┘
    
    
    UDP - Быстрый, но ненадёжный:
    ┌──────┐     ┌──────┐
    │Данные│────▶│Сервер│  Нет рукопожатия
    │  1   │     └──────┘  (быстро!)
    └──────┘
    ┌──────┐     ┌──────┐
    │Данные│────▶│ ❌   │  Может быть потерян
    │  2   │     └──────┘  (но кого это волнует, отправляем следующий!)
    └──────┘

* * *

Краткое резюме 📋
-----------------

### Пакеты vs Кадры:

    Кадр (Уровень 2)
      ├── MAC источника
      ├── MAC назначения
      └── Пакет (Уровень 3)
            ├── IP источника
            ├── IP назначения
            └── Данные

### TCP vs UDP:

    TCP = Надёжный телефонный звонок
    - Установить соединение
    - Подтвердить всё
    - Правильно повесить трубку
    
    UDP = Крикнуть через комнату
    - Просто крикнуть
    - Надеяться что услышат
    - Идти дальше

### Когда использовать:

    Используйте TCP когда:
    ✅ Данные должны прийти полностью
    ✅ Порядок важен
    ✅ Примеры: Файлы, email, веб-страницы
    
    Используйте UDP когда:
    ✅ Скорость > точность
    ✅ Реал-тайм важен
    ✅ Примеры: Стриминг, игры, звонки

* * *

Практические примеры 💡
-----------------------

### Пример 1: Веб-браузинг (TCP)

    Ваш браузер                    Веб-сервер
          |                             |
          |------ TCP Handshake ------->|  Установить соединение
          |                             |
          |------ HTTP GET / ---------->|  Запросить веб-страницу
          |                             |
          |<----- HTTP 200 OK <---------|  Отправить веб-страницу
          |<----- HTML контент <---------|
          |                             |
          |------ ACK ---------------->|  Подтвердить получение

**Почему TCP?**

* ✅ Каждый байт HTML должен прийти
* ✅ Изображения должны быть полными
* ✅ Порядок важен

* * *

### Пример 2: Видеозвонок (UDP)

    Ваш компьютер                   Компьютер друга
          |                              |
          |--- Голосовой пакет 1 (UDP) ->|  
          |--- Голосовой пакет 2 (UDP) ->|  
          |--- Голосовой пакет 3 ПОТЕРЯН! ❌
          |--- Голосовой пакет 4 (UDP) ->|  
          |--- Голосовой пакет 5 (UDP) ->|  
          |                              |
    
    Результат: Небольшой сбой звука, звонок продолжается

**Почему UDP?**

* ✅ Скорость критична (реал-тайм)
* ✅ Небольшие сбои допустимы
* ❌ Повторная отправка вызовет задержку (хуже чем потеря)

* * *

### Пример 3: Загрузка файла (TCP)

    Ваш компьютер                   Сервер загрузок
          |                              |
          |------ Запрос file.zip ------>|
          |                              |
          |<----- Пакет 1 (TCP) <--------|  ✅ Получен
          |<----- Пакет 2 (TCP) <--------|  ✅ Получен
          |<----- Пакет 3 (TCP) <--------|  ❌ Потерян!
          |                              |
          |------ "Переслать Пакет 3" --->|  TCP обнаруживает потерю
          |                              |
          |<----- Пакет 3 (TCP) <--------|  ✅ Переотправлен
          |<----- Пакет 4 (TCP) <--------|  ✅ Получен
          |                              |
    
    Результат: Полный файл со всеми данными

**Почему TCP?**

* ✅ Файл должен быть на 100% полным
* ✅ Даже один пропущенный байт = повреждённый файл
* ✅ Надёжность > Скорость

* * *

Аналогии из реальной жизни 🌍
-----------------------------

### TCP = Заказное письмо 📬

    Вы: Пишете письмо и отправляете заказное
    Почта: "Распишитесь здесь, мы будем отслеживать"
                 ↓
    Почта: Доставляет в пункт назначения
                 ↓
    Получатель: Расписывается за получение
                 ↓
    Почта: "Подтверждено доставлено!" (отправляет квитанцию)
                 ↓
    Вы: Получаете подтверждение
    
    ✅ Гарантированная доставка
    ✅ Отслеживается на каждом шаге
    ❌ Медленно и дорого

### UDP = Бросок бумажного самолётика ✈️

    Вы: Пишете записку и бросаете бумажный самолётик
                 ↓
    Самолётик летит по воздуху
                 ↓
    Может долететь до друга ✅
    Может удариться о стену и упасть ❌
    Может кто-то другой поймает ❓
                 ↓
    Вы: Не знаете, долетел ли он, и не волнуетесь
    
    ✅ Быстро и просто
    ❌ Нет гарантии
    ❌ Нет подтверждения

* * *

Ключевые выводы 🎯
------------------

### Запомните:

1. **Пакеты и кадры — разные вещи**
   
   * Пакет = Уровень 3 (IP-адреса)
   * Кадр = Уровень 2 (MAC-адреса)

2. **TCP — надёжный, но медленный**
   
   * Трёхстороннее рукопожатие
   * Гарантирует доставку
   * Использовать для файлов, веб, email

3. **UDP — быстрый, но ненадёжный**
   
   * Без установления соединения
   * Нет гарантий доставки
   * Использовать для стриминга, игр, звонков

4. **Инкапсуляция важна**
   
   * Данные "упаковываются" на каждом уровне
   * Добавляются заголовки
   * При получении — декапсуляция

5. **Выбор протокола зависит от задачи**
   
   * Нужна надёжность? → TCP
   * Нужна скорость? → UDP
   * Критичны данные? → TCP
   * Реал-тайм? → UDP

* * *

Полная сравнительная таблица 📊
-------------------------------

| Характеристика       | Пакет         | Кадр               | TCP              | UDP              |
| -------------------- | ------------- | ------------------ | ---------------- | ---------------- |
| **Уровень OSI**      | 3 (Сетевой)   | 2 (Канальный)      | 4 (Транспортный) | 4 (Транспортный) |
| **Адресация**        | IP-адреса     | MAC-адреса         | Порты            | Порты            |
| **Размер заголовка** | 20+ байт      | Зависит            | 20-60 байт       | 8 байт           |
| **Надёжность**       | -             | -                  | Высокая          | Низкая           |
| **Скорость**         | -             | -                  | Медленная        | Быстрая          |
| **Соединение**       | -             | -                  | Требуется        | Не требуется     |
| **Применение**       | Маршрутизация | Локальная доставка | Файлы, веб       | Стриминг, игры   |

* * *

Для продвинутых: Детали заголовков 🔬
-------------------------------------

### TCP Заголовок (подробно):

    ┌────────────────────────────────────────┐
    │ Порт источника (16 бит)                │
    ├────────────────────────────────────────┤
    │ Порт назначения (16 бит)               │
    ├────────────────────────────────────────┤
    │ Порядковый номер (32 бита)             │
    ├────────────────────────────────────────┤
    │ Номер подтверждения (32 бита)          │
    ├────────────────────────────────────────┤
    │ Смещение | Резерв | Флаги | Окно      │
    │          |        | SYN   |           │
    │          |        | ACK   |           │
    │          |        | FIN   |           │
    ├────────────────────────────────────────┤
    │ Контрольная сумма | Срочный указатель  │
    ├────────────────────────────────────────┤
    │ Опции (переменная длина)               │
    ├────────────────────────────────────────┤
    │                                        │
    │         Данные                         │
    │                                        │
    └────────────────────────────────────────┘
    
    Минимум: 20 байт
    Максимум: 60 байт (с опциями)

### UDP Заголовок (подробно):

    ┌────────────────────────────────────────┐
    │ Порт источника (16 бит)                │
    ├────────────────────────────────────────┤
    │ Порт назначения (16 бит)               │
    ├────────────────────────────────────────┤
    │ Длина (16 бит)                         │
    ├────────────────────────────────────────┤
    │ Контрольная сумма (16 бит)             │
    ├────────────────────────────────────────┤
    │                                        │
    │         Данные                         │
    │                                        │
    └────────────────────────────────────────┘
    
    Всегда: 8 байт

* * *

Заключение 🎓
-------------

Теперь вы понимаете:

✅ Разницу между пакетами и кадрами✅ Как работает TCP (трёхстороннее рукопожатие)✅ Как работает UDP (без соединения)✅ Когда использовать TCP vs UDP✅ Структуру заголовков✅ Процесс инкапсуляции/декапсуляции

**Помните:**

* Пакеты и кадры делают сеть эффективной

* TCP = надёжность (файлы, веб, email)

* UDP = скорость (стриминг, игры, звонки)

* Выбор протокола зависит от требований приложения

*  
