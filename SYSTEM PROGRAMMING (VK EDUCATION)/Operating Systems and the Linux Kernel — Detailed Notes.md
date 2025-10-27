🧠 Операционные системы и ядро Linux
====================================

_(Operating Systems and the Linux Kernel — Detailed Notes)_

* * *

🇷🇺 Русская версия (подробно)
------------------------------

* * *

### 1️⃣ Что включает в себя термин «Операционная система»

**Операционная система (ОС)** — это комплекс программ, управляющих аппаратными ресурсами компьютера и предоставляющих пользователю и приложениям удобный интерфейс для работы с ними.  
Она является промежуточным слоем между **пользователем/программами** и **аппаратным обеспечением**.

#### 🔧 Основные задачи ОС:

1. **Управление процессами** — создание, выполнение, приостановка и завершение процессов.

2. **Управление памятью** — выделение, освобождение, виртуальная память, кэширование.

3. **Управление устройствами** — драйверы обеспечивают единый интерфейс к аппаратуре (диски, клавиатура, сеть, видео и т.д.).

4. **Управление файловыми системами** — организация хранения данных и доступ к ним.

5. **Управление пользователями и правами доступа** — разделение прав, безопасность, аутентификация.

6. **Обеспечение интерфейсов** — API для приложений (системные вызовы), пользовательские интерфейсы (CLI, GUI).

7. **Коммуникация между процессами** — обмен данными, синхронизация, очереди, каналы.

#### 💬 Другими словами:

> ОС = ядро + системные библиотеки + утилиты + интерфейсы пользователя.

* * *

### 2️⃣ Компоненты ядра Linux

Ядро Linux — это **монолитное ядро**, содержащее все основные подсистемы операционной системы. Оно управляет ресурсами и реализует системные вызовы, через которые программы взаимодействуют с системой.

* * *

#### 🧩 1. Управление процессами (Process Management)

* Процесс — это исполняемая программа со своим адресным пространством, ресурсами и состоянием.

* Ядро управляет созданием (`fork`, `clone`), завершением (`exit`), приостановкой, возобновлением процессов.

* Каждый процесс имеет **PID**, приоритет, состояние (RUNNING, SLEEPING, ZOMBIE и др.).

* Существует иерархия процессов — каждый процесс имеет родителя.

* Linux поддерживает **потоки (threads)** через `clone()` — у них общее адресное пространство, но отдельные контексты выполнения.

📘 **Основные структуры:**

* `task_struct` — структура, описывающая процесс.

* Планировщик (scheduler) решает, какой процесс выполняется дальше.

* * *

#### ⚙️ 2. Работа с оборудованием (Device Management)

* Все устройства представлены в виде **файлов** в `/dev`.

* Ядро взаимодействует с ними через **драйверы**.

* Разделение на типы:
  
  * **Блочные устройства** (диски, SSD) — работают с блоками данных.
  
  * **Символьные устройства** (терминалы, мышь) — передают поток байтов.
  
  * **Сетевые устройства** — управляются отдельной подсистемой (netdev).

📘 **Архитектура драйверов:**

* Поддержка динамической загрузки (модули `.ko`).

* Унифицированные API через `struct file_operations`, `struct device_driver`.

* * *

#### ⏱️ 3. Работа со временем (Time Management)

* Ядро отслеживает время с помощью **счётчиков тиков** и **таймеров**.

* Основные функции:
  
  * учёт времени выполнения процессов;
  
  * планирование событий (таймеры, sleep);
  
  * подсчёт аптайма, системных метрик;
  
  * синхронизация системного времени (NTP).

📘 **Основные структуры:**

* `jiffies` — счётчик тиков (единицы времени ядра).

* `ktime_t` — представление времени в наносекундах.

* * *

#### 📂 4. Файловая система (Filesystem Management)

* Единое древо каталогов (`/` как корень).

* Все устройства и разделы монтируются в эту иерархию.

* Поддержка множества файловых систем: `ext4`, `XFS`, `Btrfs`, `FAT`, `NTFS`, `procfs`, `sysfs` и др.

📘 **Архитектура:**

* Абстрактный слой **VFS (Virtual Filesystem Switch)** — единый API для всех типов ФС.

* Каждая ФС реализует функции через структуру `super_operations`, `inode_operations`, `file_operations`.

* Поддержка **кеширования** (`page cache`) и **буферизации** для повышения производительности.

* * *

#### 🔁 5. IPC — Межпроцессное взаимодействие (Inter-Process Communication)

Позволяет процессам обмениваться данными и синхронизировать действия.

📘 **Основные механизмы в Linux:**

* **Pipes (каналы)** — поток байтов между процессами.

* **Message queues (очереди сообщений)** — обмен структурированными сообщениями.

* **Shared memory (общая память)** — общие участки RAM для быстрого обмена.

* **Semaphores / Mutexes / Spinlocks** — синхронизация доступа.

* **Signals** — уведомления процессам о событиях (например, `SIGKILL`, `SIGINT`).

* **Sockets** — для сетевого взаимодействия (локального или через TCP/IP).

* * *

#### 🌐 6. Сетевая подсистема (Networking)

* Поддерживает огромное количество протоколов (TCP/IP, UDP, ARP, ICMP, IPv6, Unix sockets и др.).

* Имеет модульную архитектуру: сетевые интерфейсы → протокольные стеки → сокеты.

* Сетевая подсистема тесно связана с планировщиком и файловыми дескрипторами (всё — «файл»).

📘 **Структуры:**

* `struct net_device` — сетевой интерфейс.

* `struct sk_buff` — буфер сетевых пакетов.

* * *

#### 👥 7. Подсистема пользователей и прав доступа

* Linux — многопользовательская система.

* Каждый пользователь имеет **UID**, **GID** и права доступа (rwx).

* Есть **суперпользователь (root)** с UID 0.

* Используется модель **Discretionary Access Control (DAC)** и механизмы **Mandatory Access Control (MAC)** через SELinux/AppArmor.

* Поддержка **capabilities** — ограниченных прав root для процессов.

* * *

#### 🧮 8. Внутренние структуры данных

В ядре повсеместно применяются собственные структуры данных для скорости и экономии памяти:

| Назначение                   | Структура      | Аналог в C           |
| ---------------------------- | -------------- | -------------------- |
| Очереди процессов            | `list_head`    | двусвязный список    |
| Таблицы и кэши               | `hash_table`   | хеш-таблица          |
| Деревья памяти, планировщика | `rb_tree`      | красно-чёрное дерево |
| Очереди событий              | `wait_queue`   | очередь ожидания     |
| Буферы файлов                | `page` / `bio` | буфер страницы/блока |

* * *

### 3️⃣ Что такое планировщик процессов и зачем он нужен

**Планировщик (Scheduler)** — это компонент ядра, который решает, **какой процесс будет выполняться следующим** и **как распределять процессорное время** между всеми активными задачами.

#### 📌 Основные цели планировщика:

* Обеспечить **справедливость** (каждый процесс получает своё время).

* Максимизировать **производительность** (эффективное использование CPU).

* Минимизировать **задержки** для интерактивных задач.

* Поддерживать **реальное время (RT)** для задач с временными ограничениями.

#### 🧠 Принципы работы:

1. Каждый процесс имеет **приоритет** (nice, real-time priority).

2. Планировщик выбирает процесс с наибольшим приоритетом или наименьшей нагрузкой.

3. В Linux используется **Completely Fair Scheduler (CFS)** — "полностью справедливый планировщик".
   
   * Он моделирует процесс как точку на временной линии виртуального времени (virtual runtime).
   
   * Каждый процесс получает долю CPU, пропорциональную своему приоритету.

📘 **Реализация:**

* Структура `struct sched_entity` описывает состояние задачи.

* Используется **красно-чёрное дерево** (`rb_tree`) для хранения активных процессов и быстрого выбора следующего.

* Специальные классы планировщиков:
  
  * `SCHED_NORMAL` (обычные задачи),
  
  * `SCHED_FIFO`, `SCHED_RR` (реального времени),
  
  * `SCHED_IDLE`, `SCHED_BATCH`.

#### 🕹️ Пример:

> Если пользователь слушает музыку, а в фоне компилируется программа, планировщик гарантирует, что музыка не будет "лагать", даже если компиляция нагружает CPU.

* * *

### 💡 Итоги (RU)

* ОС — это посредник между программами и "железом", управляющий всеми ресурсами.

* Ядро Linux — комплекс подсистем: процессы, устройства, память, файловые системы, IPC, сеть, пользователи.

* Планировщик — мозг ядра, который обеспечивает баланс между скоростью, отзывчивостью и справедливостью.

* * *

🇬🇧 English Version (Detailed)
-------------------------------

* * *

### 1️⃣ What is an Operating System

An **Operating System (OS)** is a set of programs that manage hardware resources and provide services for software and users. It acts as a **bridge** between the user/programs and the hardware.

#### Main responsibilities:

1. Process management — create, run, and terminate processes.

2. Memory management — allocate, free, and virtualize memory.

3. Device management — uniform access via drivers.

4. File system management — organize and access data.

5. User and permission control — authentication, access rights.

6. Interfaces — system APIs, shell, GUI.

7. Interprocess communication — data exchange, synchronization.

> In short:  
> **OS = Kernel + Libraries + Utilities + Interfaces**

* * *

### 2️⃣ Linux Kernel Components

The **Linux kernel** is a **monolithic kernel** — all major subsystems are built-in, with modular support. It provides system calls to bridge user-space and hardware.

#### 🧩 1. Process Management

* Processes are independent execution units with their own address spaces.

* Kernel manages creation (`fork`), termination (`exit`), suspension/resume.

* Each has a **PID**, priority, and state.

* Threads share the same memory (`clone()`).

**Data structure:** `task_struct`.  
**Scheduler** decides which process runs next.

* * *

#### ⚙️ 2. Device Management

* Devices represented as files in `/dev`.

* Accessed via **drivers**, categorized as:
  
  * Block devices (disks),
  
  * Character devices (terminals),
  
  * Network devices (NICs).

Drivers use `struct file_operations` and can be loaded dynamically as modules (`.ko`).

* * *

#### ⏱️ 3. Time Management

* Uses **ticks**, **timers**, and **NTP** synchronization.

* Responsible for process timing, scheduling events, uptime tracking.

**Structures:** `jiffies`, `ktime_t`.

* * *

#### 📂 4. Filesystem

* Unified directory tree (`/`).

* Managed by **VFS (Virtual Filesystem Switch)** — common API for multiple FS types.

* Supports caching (`page cache`), journaling, and mounting.

* Supports many FS: ext4, XFS, Btrfs, procfs, sysfs, etc.

* * *

#### 🔁 5. IPC (Inter-Process Communication)

Mechanisms for data sharing and synchronization:

* Pipes, message queues, shared memory

* Semaphores, mutexes, spinlocks

* Signals (event notifications)

* Sockets (local & network)

* * *

#### 🌐 6. Networking

* Modular networking stack supporting TCP/IP, UDP, IPv6, etc.

* Integrated with file descriptor model.

* Uses `struct net_device` and `struct sk_buff`.

* * *

#### 👥 7. Users and Permissions

* Multiuser model (UID/GID).

* Root = UID 0.

* DAC and MAC (SELinux/AppArmor).

* Fine-grained privileges via **capabilities**.

* * *

#### 🧮 8. Internal Data Structures

| Purpose        | Structure     | Type                 |
| -------------- | ------------- | -------------------- |
| Process lists  | `list_head`   | doubly linked list   |
| Scheduler tree | `rb_tree`     | red-black tree       |
| Caches         | `hash_table`  | hash map             |
| Wait queues    | `wait_queue`  | event queue          |
| Buffers        | `page`, `bio` | memory/block buffers |

* * *

### 3️⃣ Process Scheduler — Role and Design

**Scheduler** decides which process executes next and how CPU time is distributed.

#### Goals:

* Fairness

* Performance efficiency

* Low latency for interactive tasks

* Real-time support

#### Operation:

* Each process has a **priority**.

* Scheduler picks the process with the lowest virtual runtime.

* Linux uses **CFS (Completely Fair Scheduler)**.
  
  * Models processes as entities in a red-black tree by virtual runtime.
  
  * Each gets CPU time proportional to its weight (priority).

**Structures:** `sched_entity`, `rb_tree`.  
**Classes:** `SCHED_NORMAL`, `SCHED_RR`, `SCHED_FIFO`, `SCHED_IDLE`.

#### Example:

> The scheduler ensures smooth audio playback even when the system compiles large codebases.

* * *

### 💡 Takeaways (EN)

* The OS manages all hardware and system resources.

* The Linux kernel is a unified, modular engine handling processes, files, IPC, network, users.

* The scheduler balances responsiveness and throughput — core to system performance.
