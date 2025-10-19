# 📡 HTTP / HTTPS

## 🇷🇺 Русская версия

### 1. Определение — главное

**HTTP** — прикладной протокол для запроса и передачи ресурсов (HTML, CSS, JS, изображения) между клиентом (браузером) и сервером.  
**HTTPS** = HTTP поверх TLS — тот же HTTP, но по зашифрованному каналу (конфиденциальность + целостность + аутентификация сервера).

**Ключевая последовательность (запомнить):** DNS → TCP (3-way handshake) → (TLS handshake при HTTPS) → HTTP request → HTTP response → render.

---

### 2. Общий поток загрузки страницы (упрощённо)

1. Вводишь URL → DNS решает домен → получает IP.  
2. TCP: клиент делает `SYN` → сервер `SYN-ACK` → клиент `ACK`.  
3. Если HTTPS: TLS handshake — `ClientHello` → `ServerHello` + сертификат → проверка CA → обмен ключами → сессия (session key).  
4. Клиент отправляет HTTP-запрос (метод, путь, заголовки, опциональное тело).  
5. Сервер возвращает HTTP-ответ (код состояния, заголовки, тело).  
6. Браузер парсит HTML, загружает ресурсы, выполняет JS, строит DOM/CSSOM → render.

---

### 3. Строение HTTP-запроса и ответа — кратко + пример

**Пример запроса (HTTP/1.1):** `GET / HTTP/1.1 Host: tryhackme.com User-Agent: Mozilla/5.0 Referer: https://tryhackme.com/` (пустая строка после заголовков).

- **Первая строка:** `METHOD PATH HTTP/VERSION` (например `GET /api HTTP/1.1`).  
- **Заголовки:** `Host`, `User-Agent`, `Accept`, `Content-Type`, `Cookie`, `Authorization` и др.  
- **Тело (body):** есть у `POST`, `PUT`; у `GET` обычно нет.

**Пример ответа:**
`HTTP/1.1 200 OK Server: nginx Date: Fri, 09 Apr 2021 13:34:03 GMT Content-Type: text/html Content-Length: 98`  
тело: `<html>...</html>`

- **Строка ответа:** версия + код состояния + фраза.  
- **Заголовки:** `Content-Type`, `Content-Length`, `Set-Cookie`, `Cache-Control` и др.  
- **Тело:** содержимое (HTML/CSS/JS/изображение).

---

### 4. Основные HTTP-методы

- `GET` — получить ресурс.  
- `POST` — отправить данные / создать ресурс.  
- `PUT` — обновить ресурс.  
- `DELETE` — удалить ресурс.  
- `HEAD`, `OPTIONS` — служебные (без тела / для проверки).

---

### 5. Коды состояния (важные)

- `1xx` — информационные (редко).  
- `2xx` — успех (200 OK, 201 Created).  
- `3xx` — редиректы (301 permanent, 302 temporary).  
- `4xx` — ошибки клиента (400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 405 Method Not Allowed).  
- `5xx` — ошибки сервера (500 Internal Server Error, 503 Service Unavailable).

**Практический:** в логах CTF/лаба коды часто дают подсказку: `404` — ресурс отсутствует; `405` — поменяй метод; `500` — может раскрыть стектрейс.

---

### 6. HTTPS / TLS — что важно знать

- TLS обеспечивает: **конфиденциальность**, **целостность**, **аутентификацию сервера** (через сертификат X.509).  
- Упрощённая последовательность TLS handshake: `ClientHello` (версии, шифры, рандом) → `ServerHello` + сертификат → клиент проверяет сертификат (ЦА) → договариваются об обмене ключами → получают симметричный `session key` → весь трафик шифруется.  
- Значок замочка в браузере = успешный TLS handshake (проверяй срок действия и цепочку доверия).  
- **Практика:** при проблемах смотри цепочку сертификатов и дату; в CTF часто используют просроченные или самоподписанные сертификаты.

---

### 7. Порты и URL

- По умолчанию: **HTTP → 80**, **HTTPS → 443**.  
- Формат URL: `схема://хост:порт/путь?query#fragment`. Пример: `https://example.com:8443/path?id=1#section`.  
- `Query string` (`?a=1&b=2`) — данные для GET-запросов; `fragment` (`#`) — обработка на стороне клиента.

---

### 8. Заголовки — кратко полезные

**Запросы:** `Host` (виртуальный хост), `User-Agent`, `Accept`, `Accept-Encoding`, `Content-Type`, `Content-Length`, `Cookie`, `Authorization`.  
**Ответы:** `Content-Type`, `Set-Cookie`, `Cache-Control`, `Expires`, `ETag`, `Last-Modified`, `Content-Encoding` (gzip, br).

**Практический:** если страница не обновляется — сначала проверь `Cache-Control` / `ETag`.

---

### 9. Cookie — коротко

- Небольшие данные, которые браузер хранит и отправляет с запросами на тот же домен.  
- Часто используются для сессий/аутентификации. Рекомендуемые флаги: `HttpOnly`, `Secure`, `SameSite`.  
- Просмотр через DevTools → Network → Cookies.

---

### 10. Парсинг страницы в браузере (render pipeline)

- Браузер получает HTML → строит **DOM**.  
- Загружает CSS → строит **CSSOM**.  
- Объединяет в **render tree** → layout → paint.  
- JS может блокировать парсинг, если `<script>` без `defer`/`async`.  
- **Практический:** `defer` и `async` влияют на порядок выполнения JS — важно для оптимизации.

---

### 11. Безопасность веба — быстрые определения и контрмеры

- **XSS (Cross-Site Scripting)** — внедрение/выполнение чужого JS. Защита: экранирование/валидация, CSP.  
- **CSRF (Cross-Site Request Forgery)** — подделка запросов от авторизованного пользователя. Защита: CSRF-токены, проверка `Origin`/`Referer`.  
- **MitM (Man-in-the-Middle)** — перехват трафика. Защита: правильно настроенный TLS.  
- **CORS (Cross-Origin Resource Sharing)** — политика, кто может обращаться к API; неправильные настройки — уязвимость.

**Практический:** в CTF часто ищут XSS/CSRF/неверно настроенный CORS.

---

### 12. Полезные приёмы для TryHackMe / CTF

- Читай raw request/response в DevTools (Network tab) — основной инструмент.  
- Пробуй сменить метод (GET ↔ POST), изменить заголовки (`Host`, `User-Agent`, `Referer`).  
- Проверяй cookies, session tokens и `Set-Cookie`.  
- Диагностика TLS: проверь сертификат, дату, цепочку доверия.  
- Ищи подсказки в кодах ответа (`301/302` → редирект; `405` → метод не поддерживается; `500` → может дать стек/инфо).

---

### 13. Шпаргалка (копировать в заметки)

- **Определение:** HTTP — протокол для передачи ресурсов; HTTPS = HTTP + TLS.  
- **Последовательность:** DNS → TCP(3-way) → (TLS handshake) → HTTP request → response → render.  
- **Методы:** GET, POST, PUT, DELETE, HEAD.  
- **Коды:** 2xx (успех), 3xx (редирект), 4xx (клиент), 5xx (сервер).  
- **Важные заголовки:** Host, User-Agent, Content-Type, Authorization, Cookie, Cache-Control, CSP.  
- **TLS handshake:** ClientHello → ServerHello + Cert → key-exchange → session key → шифрованный канал.  
- **Базовые угрозы/защита:** XSS → экранирование/CSP; CSRF → токены/проверка Origin; MitM → TLS; CORS → корректные заголовки.  
- **Порты:** HTTP 80, HTTPS 443.

---

## 🇬🇧 English version

### 1. Definition — the main point

**HTTP** is an application protocol for requesting and transferring resources (HTML, CSS, JS, images) between a client (browser) and a server.  
**HTTPS** = HTTP over TLS — the same HTTP but over an encrypted channel (confidentiality + integrity + server authentication).

**Key sequence (memorize):** DNS → TCP (3-way handshake) → (TLS handshake for HTTPS) → HTTP request → HTTP response → render.

---

### 2. Page load flow (simplified)

1. Enter URL → DNS resolves domain → IP returned.  
2. TCP handshake: client `SYN` → server `SYN-ACK` → client `ACK`.  
3. If HTTPS: TLS handshake — `ClientHello` → `ServerHello` + certificate → CA validation → key exchange → session key.  
4. Client sends HTTP request (method, path, headers, optional body).  
5. Server returns HTTP response (status code, headers, body).  
6. Browser parses HTML, fetches resources, runs JS, builds DOM/CSSOM → render.

---

### 3. HTTP request/response structure — short + example

**Example request (HTTP/1.1):** `GET / HTTP/1.1 Host: tryhackme.com User-Agent: Mozilla/5.0 Referer: https://tryhackme.com/` (blank line after headers).

- **Start line:** `METHOD PATH HTTP/VERSION` (e.g., `GET /api HTTP/1.1`).  
- **Headers:** `Host`, `User-Agent`, `Accept`, `Content-Type`, `Cookie`, `Authorization`.  
- **Body:** present for `POST`, `PUT`; usually empty for `GET`.

**Example response:** `HTTP/1.1 200 OK Server: nginx Date: Fri, 09 Apr 2021 13:34:03 GMT Content-Type: text/html Content-Length: 98` body: `<html>...</html>`

- **Status line:** version + status code + reason phrase.  
- **Headers:** `Content-Type`, `Content-Length`, `Set-Cookie`, `Cache-Control`.  
- **Body:** payload (HTML/CSS/JS/image).

---

### 4. Main HTTP methods

- `GET` — retrieve resource.  
- `POST` — send data / create resource.  
- `PUT` — update resource.  
- `DELETE` — delete resource.  
- `HEAD`, `OPTIONS` — utility methods.

---

### 5. Status codes (important)

- `1xx` — informational.  
- `2xx` — success (200 OK, 201 Created).  
- `3xx` — redirects (301 permanent, 302 temporary).  
- `4xx` — client errors (400, 401, 403, 404, 405).  
- `5xx` — server errors (500, 503).

**Practical:** status codes in CTF/labs reveal hints (404 — missing resource; 405 — try different method; 500 — possible stacktrace).

---

### 6. HTTPS / TLS — key points

- TLS provides **confidentiality**, **integrity**, **server authentication** (X.509 cert).  
- Simplified TLS handshake: `ClientHello` → `ServerHello` + certificate → client verifies CA → key exchange → derive symmetric session key → encrypted channel.  
- Browser padlock = successful TLS handshake (check cert validity and chain).  
- **Practice:** check certificate chain and dates; CTFs often use expired/self-signed certs.

---

### 7. Ports and URL

- Defaults: **HTTP → 80**, **HTTPS → 443**.  
- URL format: `scheme://host:port/path?query#fragment`. Example: `https://example.com:8443/path?id=1#section`.  
- Query string (`?a=1&b=2`) is for GET data; `fragment` is client-side only.

---

### 8. Headers — quick useful list

**Requests:** `Host`, `User-Agent`, `Accept`, `Accept-Encoding`, `Content-Type`, `Content-Length`, `Cookie`, `Authorization`.  
**Responses:** `Content-Type`, `Set-Cookie`, `Cache-Control`, `Expires`, `ETag`, `Last-Modified`, `Content-Encoding`.

**Practical:** if a page doesn't update, check `Cache-Control` / `ETag`.

---

### 9. Cookies — short

- Small data stored by browser and sent with requests to the same domain.  
- Used for sessions/auth. Recommended flags: `HttpOnly`, `Secure`, `SameSite`.  
- Inspect via DevTools → Network → Cookies.

---

### 10. Browser render pipeline

- Browser receives HTML → builds **DOM**.  
- Loads CSS → builds **CSSOM**.  
- Combines into **render tree** → layout → paint.  
- JS can block parsing if `<script>` without `defer`/`async`.  
- **Practical:** `defer`/`async` affect execution ordering — important for performance.

---

### 11. Web security — quick defs & mitigations

- **XSS:** injection/execution of JS. Mitigation: escaping/validation, CSP.  
- **CSRF:** forged requests by a logged-in user. Mitigation: CSRF tokens, check `Origin`/`Referer`.  
- **MitM:** traffic interception. Mitigation: properly configured TLS.  
- **CORS:** controls who can access API; misconfigurations are vulnerabilities.

**Practical:** CTFs often have XSS/CSRF/CORS misconfigs.

---

### 12. Useful techniques for TryHackMe / CTF

- Inspect raw request/response in DevTools (Network).  
- Try changing method (GET ↔ POST), tweak headers (`Host`, `User-Agent`, `Referer`).  
- Check cookies, session tokens, `Set-Cookie`.  
- TLS diagnostics: check cert, date, chain.  
- Look for hints in status codes (`301/302`, `405`, `500`).

---

### 13. Cheat-sheet (notes)

- **Definition:** HTTP — protocol for resource transfer; HTTPS = HTTP + TLS.  
- **Sequence:** DNS → TCP(3-way) → (TLS handshake) → HTTP request → response → render.  
- **Methods:** GET, POST, PUT, DELETE, HEAD.  
- **Codes:** 2xx success, 3xx redirect, 4xx client, 5xx server.  
- **Important headers:** Host, User-Agent, Content-Type, Authorization, Cookie, Cache-Control, CSP.  
- **TLS handshake:** ClientHello → ServerHello + Cert → key-exchange → session key → encrypted channel.  
- **Threats & defenses:** XSS → escape/CSP; CSRF → tokens/Origin checks; MitM → TLS; CORS → proper headers.  
- **Ports:** HTTP 80, HTTPS 443.

---
