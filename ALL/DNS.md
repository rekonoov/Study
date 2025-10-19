# 🌐 Система доменных имён (DNS) / Domain Name System

## 🇷🇺 Русская версия

### 💡 Что такое DNS

DNS (Domain Name System) — это система, которая переводит понятные человеку доменные имена, например tryhackme.com, в IP-адреса, например 104.26.10.229, чтобы устройства могли находить друг друга в Интернете.

**Аналогия:**  
Как адрес дома нужен для доставки писем, так и IP-адрес нужен, чтобы данные доходили до нужного компьютера. Вместо сложных чисел мы запоминаем удобные имена, например tryhackme.com.

---

### 🧩 Структура доменного имени

#### 1. TLD (Домен верхнего уровня)

Находится в конце домена (справа от точки), например tryhackme.com — TLD = .com.

Типы TLD:  

- gTLD — общие домены: .com, .org, .edu, .gov  
- ccTLD — национальные: .ru, .jp, .de, .co.uk, .ca  
  Сейчас существует более 2000 TLD, включая новые: .club, .biz, .online и др.

#### 2. Домен второго уровня

Это основное имя сайта, которое идёт перед TLD, например tryhackme.com — домен второго уровня tryhackme.

Ограничения:  

- максимум 63 символа  
- можно использовать a-z, 0-9, -  
- нельзя начинать или заканчиваться на -, нельзя ставить подряд несколько дефисов

#### 3. Субдомен

Находится слева от домена второго уровня, например admin.tryhackme.com — субдомен = admin. Можно использовать несколько субдоменов, например jupiter.servers.tryhackme.com.

Правила:  

- ≤ 63 символов  
- только a-z, 0-9, -  
- нельзя начинать/заканчивать на -  
- общая длина домена ≤ 253 символов

---

### 🧱 Типы DNS-записей

- **A** — указывает IPv4-адрес, например 104.26.10.229  
- **AAAA** — указывает IPv6-адрес, например 2606:4700:20::681a:be5  
- **CNAME** — ссылка на другое доменное имя, например store.tryhackme.com → shops.shopify.com  
- **MX** — почтовый сервер домена, например alt1.aspmx.l.google.com (с приоритетом)  
- **TXT** — текстовые данные, такие как SPF, DKIM, верификация, например v=spf1 include:_spf.google.com ~all  

**Примечание:**  
Записи MX и TXT часто используются для защиты от спама, проверки владения доменом и маршрутизации почты.

---

### ⚙️ Как работает DNS-запрос

1. **Проверка локального кэша** — компьютер проверяет, запрашивался ли этот домен недавно. Если запись есть, используется локальная копия без обращения в Интернет.  
2. **Обращение к рекурсивному DNS-серверу** — если записи нет, запрос уходит к серверу провайдера, который может иметь свой кэш. Если запись найдена — возвращается сразу.  
3. **Корневой сервер (Root DNS)** — если запись не найдена, рекурсивный сервер обращается к корневому серверу, который знает, где находятся TLD-серверы (.com, .org, .ru и т.д.).  
4. **Сервер домена верхнего уровня (TLD)** — TLD-сервер направляет запрос к авторитетному серверу имён домена. Например для tryhackme.com это kip.ns.cloudflare.com и uma.ns.cloudflare.com.  
5. **Авторитетный DNS-сервер** — сервер, где хранятся актуальные DNS-записи для домена. Он возвращает нужный IP-адрес обратно рекурсивному серверу.  
6. **Кэширование результата** — рекурсивный сервер сохраняет запись в кэше на определённое время, заданное TTL (Time To Live) в секундах. Это снижает нагрузку на сеть: повторные запросы не обращаются заново к DNS.  
7. **Ответ пользователю** — рекурсивный сервер возвращает результат компьютеру, и браузер подключается напрямую к нужному IP-адресу.

---

### 🧠 Итог

| Элемент             | Назначение                                     |
| ------------------- | ---------------------------------------------- |
| DNS                 | Преобразует имена доменов в IP-адреса          |
| TLD                 | Домен верхнего уровня (.com, .org, .ru)        |
| 2-й уровень         | Основное имя домена (tryhackme)                |
| Субдомен            | Дополнительное имя слева (admin.tryhackme.com) |
| A / AAAA            | Записи для IPv4 / IPv6                         |
| MX / TXT            | Почтовые и служебные записи                    |
| CNAME               | Псевдоним домена                               |
| TTL                 | Время кэширования записи                       |
| Авторитетный сервер | Хранит оригинальные DNS-записи                 |
| Рекурсивный сервер  | Делает все запросы и кэширует результат        |

**Ключевая мысль:**  
DNS — это "телефонная книга Интернета", где доменные имена, например google.com, связаны с IP-адресами серверов.

---

## 🇬🇧 English version

### 💡 What is DNS

DNS (Domain Name System) is a system that translates human-readable domain names, like tryhackme.com, into IP addresses, like 104.26.10.229, so devices can find each other on the Internet.

**Analogy:**  
Like a home address is needed for delivering mail, an IP address is needed for routing data to the correct computer. Instead of remembering numbers, we use names such as tryhackme.com.

---

### 🧩 Domain Name Structure

#### 1. TLD (Top-Level Domain)

Located at the end of the domain, e.g., tryhackme.com → TLD = .com.  

Types of TLDs:  

- gTLD — generic domains: .com, .org, .edu, .gov  
- ccTLD — country domains: .ru, .jp, .de, .co.uk, .ca  
  There are over 2000 TLDs, including new ones like .club, .biz, .online.

#### 2. Second-Level Domain

The main site name before the TLD, e.g., tryhackme.com → tryhackme.  

Rules:  

- max 63 characters  
- allowed: a-z, 0-9, -  
- cannot start/end with -, no consecutive hyphens

#### 3. Subdomain

Located to the left of the second-level domain, e.g., admin.tryhackme.com → subdomain = admin. Multiple subdomains allowed, e.g., jupiter.servers.tryhackme.com.  

Rules:  

- ≤ 63 characters  
- only a-z, 0-9, -  
- cannot start/end with -  
- total domain length ≤ 253 characters

---

### 🧱 DNS Record Types

- **A** — points to IPv4 address, e.g., 104.26.10.229  
- **AAAA** — points to IPv6 address, e.g., 2606:4700:20::681a:be5  
- **CNAME** — alias to another domain, e.g., store.tryhackme.com → shops.shopify.com  
- **MX** — mail server, e.g., alt1.aspmx.l.google.com (with priority)  
- **TXT** — text data such as SPF, DKIM, verification, e.g., v=spf1 include:_spf.google.com ~all  

**Note:**  
MX and TXT records are often used for spam protection, domain ownership verification, and mail routing.

---

### ⚙️ How DNS Query Works

1. **Local cache check** — computer checks its cache. If the record exists, it's used without accessing the Internet.  
2. **Recursive DNS server** — query is sent to ISP server, which may have cached records.  
3. **Root DNS server** — if not found, the recursive server queries the root DNS server, which knows where TLD servers are.  
4. **TLD server** — forwards the query to the authoritative name server. Example for tryhackme.com: kip.ns.cloudflare.com, uma.ns.cloudflare.com.  
5. **Authoritative DNS server** — stores the real DNS records and returns the IP to the recursive server.  
6. **Caching** — recursive server stores the record for TTL (Time To Live) in seconds, reducing network load.  
7. **Response to user** — browser connects directly to the IP address.

---

### 🧠 Summary

| Element              | Purpose                                      |
| -------------------- | -------------------------------------------- |
| DNS                  | Converts domain names to IP addresses        |
| TLD                  | Top-level domain (.com, .org, .ru)           |
| 2nd-level domain     | Main domain name (tryhackme)                 |
| Subdomain            | Extra name on the left (admin.tryhackme.com) |
| A / AAAA             | IPv4 / IPv6 records                          |
| MX / TXT             | Mail and service records                     |
| CNAME                | Domain alias                                 |
| TTL                  | Caching duration                             |
| Authoritative server | Stores original DNS records                  |
| Recursive server     | Queries and caches results                   |

**Key takeaway:**  
DNS is the "Internet phonebook," linking domain names, e.g., google.com, to server IP addresses.
