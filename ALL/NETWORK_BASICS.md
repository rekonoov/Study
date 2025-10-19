# 🌐 Основы компьютерных сетей (Networking Basics)

## 🇷🇺 Русская версия

### 1️⃣ Введение в сети

**Компьютерная сеть** — система, объединяющая устройства (компьютеры, серверы, маршрутизаторы, принтеры и др.) для обмена данными и совместного использования ресурсов.

**Зачем нужны сети:**

- Передача данных между устройствами
- Совместное использование оборудования (принтеров, хранилищ)
- Доступ к интернету и внешним сервисам

**Типы сетей по охвату:**

| Тип | Расшифровка           | Описание                             | Пример                             |
| --- | --------------------- | ------------------------------------ | ---------------------------------- |
| LAN | Local Area Network    | Локальная сеть в пределах офиса/дома | Домашняя сеть, офис                |
| WAN | Wide Area Network     | Глобальная сеть, соединяющая регионы | Интернет                           |
| PAN | Personal Area Network | Персональная мини-сеть               | Смартфон + ноутбук через Bluetooth |

---

### 2️⃣ Компоненты сети

**🖥️ Устройства:**

- Компьютеры, серверы
- Принтеры, сканеры
- Коммутаторы (Switches), маршрутизаторы (Routers)

**🔌 Среда передачи данных:**

- Проводные — Ethernet, оптоволокно (надежно и быстро)  
- Беспроводные — Wi-Fi, Bluetooth, радиоканалы

**📡 Протоколы (основа коммуникации):**

| Протокол   | Назначение                  |
| ---------- | --------------------------- |
| TCP/IP     | Базовый стек интернета      |
| HTTP/HTTPS | Веб-коммуникации            |
| FTP        | Передача файлов             |
| DNS        | Преобразование доменов в IP |

---

### 3️⃣ Типы соединений

**🧷 Проводные:**

- Высокая стабильность и скорость
- Меньше подвержены шумам
- Используются в офисах, серверах, дата-центрах

**📶 Беспроводные:**

- Удобство и мобильность
- Зависимость от сигнала, помех
- Примеры: Wi-Fi, Bluetooth

---

### 4️⃣ Основы работы сети

**🔹 IP-адрес (Internet Protocol)**

- Уникальный идентификатор устройства
- Необходим для доставки пакетов данных

| Версия | Длина   | Пример                         |
| ------ | ------- | ------------------------------ |
| IPv4   | 32 бита | 192.168.0.1                    |
| IPv6   | 128 бит | 2001:0db8:85a3::8a2e:0370:7334 |

**🔹 MAC-адрес (Media Access Control)**

- Уникальный физический адрес сетевой карты
- Формат: `00:1A:2B:3C:4D:5E`
- Используется внутри LAN, назначается производителем

**🔹 TCP (Transmission Control Protocol)**

- Надежный транспортный протокол с проверкой целостности и порядком пакетов
- Используется в HTTP/HTTPS, SMTP, FTP
- **Пример:** браузер отправляет TCP-пакеты при загрузке сайта; сервер подтверждает получение (ACK)

**🔹 UDP (User Datagram Protocol)**

- Быстрее TCP, без проверки доставки и порядка
- Используется в видеопотоках, играх, VoIP
- **Пример:** онлайн-игры используют UDP для минимизации задержек

**🔹 DNS (Domain Name System)**

- Перевод доменных имен в IP
- **Как работает:**
  1. Пользователь вводит `google.com`
  2. Компьютер запрашивает DNS-сервер
  3. Сервер возвращает IP, например `142.250.74.14`
  4. Устанавливается соединение по IP
- **Аналогия:** DNS — «телефонная книга» интернета

**🔹 Ping**

- Проверка доступности хоста и задержки соединения
- Отправляет ICMP Echo Request → получает Echo Reply → измеряет RTT
- **Пример:** `ping 8.8.8.8`

---

### 5️⃣ Безопасность сетей

**🔒 Шифрование:** защищает данные от перехвата (HTTPS, VPN, SSH)  
**🧑‍💻 Аутентификация:** проверка личности (логин/пароль, токены, сертификаты)  
**🔥 Брандмауэры и антивирусы:** фильтрация трафика, блокировка подозрительных соединений

**Основные принципы защиты:**

- Минимизация доступа — только нужные права
- Регулярное обновление ПО
- Мониторинг трафика — анализ логов, IDS/IPS

---

### 6️⃣ Ключевые команды для диагностики

| Команда              | Назначение                            |
| -------------------- | ------------------------------------- |
| ping                 | Проверка доступности IP/домена        |
| traceroute / tracert | Проверка маршрута до хоста            |
| ip addr / ifconfig   | Просмотр IP и сетевых интерфейсов     |
| netstat -tuln        | Просмотр активных соединений и портов |
| nslookup / dig       | Проверка DNS-записей                  |
| curl / wget          | Отправка HTTP-запросов                |

---

### 7️⃣ Итог

Компьютерные сети — основа Интернета. Для Backend / InfoSec важно понимать:

- Как устройства обмениваются данными
- Как работают IP, TCP, DNS
- Как тестировать и защищать сеть

**Даже при изучении кибербезопасности большинство атак (MITM, DDoS, DNS Spoofing) опираются на эти принципы.**

**🚀 Быстрая шпаргалка**

| Понятие     | Определение                                 |
| ----------- | ------------------------------------------- |
| IP          | Адрес устройства в сети                     |
| MAC         | Уникальный адрес сетевой карты              |
| TCP         | Надёжный протокол с подтверждением доставки |
| UDP         | Быстрый протокол без проверки               |
| DNS         | Преобразует домены в IP                     |
| Ping        | Проверка доступности устройства             |
| LAN/WAN/PAN | Локальная / Глобальная / Персональная сеть  |
| HTTPS/VPN   | Защищённая передача данных                  |
| Firewall    | Фильтрация входящего/исходящего трафика     |

---

## 🇬🇧 English version

### 1️⃣ Introduction to Networks

**Computer network** — a system connecting devices (computers, servers, routers, printers) to exchange data and share resources.

**Why networks are needed:**

- Data transmission between devices
- Shared access to equipment (printers, storage)
- Internet and external services access

**Network types by coverage:**

| Type | Full Name             | Description                                 | Example                           |
| ---- | --------------------- | ------------------------------------------- | --------------------------------- |
| LAN  | Local Area Network    | Local network within an office/home         | Home network, office              |
| WAN  | Wide Area Network     | Global network connecting regions/countries | Internet                          |
| PAN  | Personal Area Network | Personal mini-network                       | Smartphone + laptop via Bluetooth |

---

### 2️⃣ Network Components

**🖥️ Devices:**

- Computers, servers
- Printers, scanners
- Switches, routers

**🔌 Transmission medium:**

- Wired — Ethernet, fiber (reliable & fast)  
- Wireless — Wi-Fi, Bluetooth, radio channels

**📡 Protocols:**

| Protocol   | Purpose                 |
| ---------- | ----------------------- |
| TCP/IP     | Core internet stack     |
| HTTP/HTTPS | Web communication       |
| FTP        | File transfer           |
| DNS        | Converts domains to IPs |

---

### 3️⃣ Connection Types

**🧷 Wired:**

- Stable and fast
- Less prone to noise
- Used in offices, servers, data centers

**📶 Wireless:**

- Convenient and mobile
- Signal-dependent, prone to interference
- Examples: Wi-Fi, Bluetooth

---

### 4️⃣ Network Basics

**🔹 IP Address**

- Unique identifier for a device
- Needed for delivering data packets

| Version | Length  | Example                        |
| ------- | ------- | ------------------------------ |
| IPv4    | 32-bit  | 192.168.0.1                    |
| IPv6    | 128-bit | 2001:0db8:85a3::8a2e:0370:7334 |

**🔹 MAC Address**

- Unique physical address of network card
- Format: `00:1A:2B:3C:4D:5E`
- Used inside LAN, assigned by manufacturer

**🔹 TCP**

- Reliable transport protocol with delivery guarantees
- Ensures packet order and integrity
- Used in HTTP/HTTPS, SMTP, FTP

**Example:** Browser sends TCP packets when loading a site; server ACKs receipt.

**🔹 UDP**

- Faster than TCP, no delivery/order check
- Used in video streaming, gaming, VoIP
- Example: Online games use UDP for minimal delay

**🔹 DNS**

- Converts domain names → IP addresses
- **How it works:**
  1. User types `google.com`
  2. Computer queries DNS server
  3. Server returns IP e.g., `142.250.74.14`
  4. Connection established via IP
- **Analogy:** DNS is the Internet’s “phone book”

**🔹 Ping**

- Checks host availability & latency
- Sends ICMP Echo Request → receives Echo Reply → measures RTT
- **Example:** `ping 8.8.8.8`

---

### 5️⃣ Network Security

**🔒 Encryption:** protects data from interception (HTTPS, VPN, SSH)  
**🧑‍💻 Authentication:** verifies user identity (login/password, tokens, certificates)  
**🔥 Firewalls & antivirus:** traffic filtering, block suspicious connections

**Core security principles:**

- Minimize access — only necessary permissions
