# 💉 HTML-инъекция (HTML Injection)

## 🇷🇺 Русская версия

### ⚡ Что это такое

HTML-инъекция — уязвимость, возникающая, когда веб-сайт отображает пользовательские данные без фильтрации или экранирования. Если сервер или клиентская часть вставляют введённый пользователем текст прямо в HTML-страницу, злоумышленник может внедрить свой HTML или JavaScript и изменить содержимое/поведение страницы.

Проще: если сайт вставляет ввод "как есть", пользователь может добавить ссылки, заголовки, скрипты и т.д.

---

### 🧠 Механизм работы

1. Пользователь вводит текст в форму (например, поле `username`).  
2. Приложение отображает этот ввод в HTML-странице без проверки.  
3. Браузер воспринимает текст как HTML, если он содержит теги.  
4. В результате злоумышленник может внедрить HTML/JS и изменить внешний вид или поведение страницы.

---

### 💻 Пример (вставлено прямо в текст)

Форма: `<form> <input type="text" name="username"> <button>Say Hi!</button></form>`

JS, который берёт ввод и вставляет в страницу: `element.innerHTML = "Hello, " + name;`

Если пользователь введёт `<a href="http://evil.com">Hacker</a>`, то страница выведет: `Hello, Hacker` — и `Hacker` будет полноценной ссылкой на `http://evil.com`, потому что тег был интерпретирован браузером.

Если возможно вставить `<script>…</script>`, то инъекция превращается в XSS — код исполнится в контексте страницы.

---

### ⚠️ Почему это опасно

- Изменение внешнего вида сайта (вставка текста, картинок, кнопок).  
- Фишинг — внедрение злонамеренных форм/ссылок (например, “введите пароль ещё раз”).  
- XSS — исполнение скриптов в браузере жертвы (кража cookies, сессий, выполнение действий от имени пользователя).

---

### 🧰 Как предотвращать (главные правила)

**Никогда не доверяй пользовательскому вводу.**

1. **Очистка данных (sanitization)** — удаляй или фильтруй HTML-теги перед вставкой. Пример простой функции:
   `function sanitize(input) { return input.replace(/<[^>]*>/g, ""); }`

2. **Экранирование (encoding)** — заменяй специальные символы в HTML:  
   `<` → `&lt;`, `>` → `&gt;`, `"` → `&quot;`, `'` → `&#39;`.

3. **Безопасные методы вывода** — в браузере используйте `textContent` вместо `innerHTML`:  
   `element.textContent = userInput; // безопасно`

4. **Шаблонизаторы с автоэкранированием** — серверные шаблонизаторы (Django, Jinja2, EJS и т.п.) по умолчанию экранируют вывод — используйте их настройки.

5. **Whitelist-валидация** — если допускаются только определённые теги/атрибуты, применяйте белый список (например, для WYSIWYG с огранничениями).

---

### 🧩 Отличие от SQL-инъекции

| Характеристика | HTML-инъекция                    | SQL-инъекция                       |
| -------------- | -------------------------------- | ---------------------------------- |
| Где происходит | На стороне клиента (в браузере)  | На стороне сервера (в БД)          |
| Что изменяет   | Внешний вид и поведение страницы | Запросы к базе данных, данные      |
| Цель           | Манипуляция интерфейсом, фишинг  | Кража/изменение данных, обход auth |
| Тип атаки      | Визуальная / XSS                 | Инъекционная / серверная           |

---

### 🧠 Итог (кратко)

- **Определение:** внедрение HTML-кода в страницу через пользовательский ввод.  
- **Причина:** отсутствие фильтрации/экранирования.  
- **Последствия:** изменение интерфейса, фишинг, XSS и кража данных в браузере.  
- **Решение:** экранирование, фильтрация (sanitization), безопасные методы вывода и шаблонизаторы с автоэкранированием.

**Аналогия:** если дать пользователю писать прямо в HTML-код страницы, он может сделать в ней всё что угодно.

**Ключевая мысль:** HTML-инъекция — это взлом доверия браузера; проверять ввод нужно всегда, даже для простого поля "имя".

---

## 🇬🇧 English version

### ⚡ What is HTML Injection

HTML injection is a vulnerability that occurs when a website renders user-supplied data without sanitization or encoding. If server or client code inserts user input directly into the page HTML, an attacker can inject HTML or JavaScript and change page content/behavior.

Simply put: if the site places input "as is" into the page, the user can add links, headings, scripts, etc.

---

### 🧠 How it works

1. User types text into a form (e.g., `username`).  
2. The application renders that input into the HTML page without validation.  
3. The browser interprets the text as HTML if it contains tags.  
4. An attacker can therefore inject HTML/JS and manipulate the page.

---

### 💻 Example (inline)

Form: `<form> <input type="text" name="username"> <button>Say Hi!</button></form>`

JS inserting input unsafely: `element.innerHTML = "Hello, " + name;`

If the user inputs `<a href="http://evil.com">Hacker</a>`, the page displays `Hello, Hacker` and `Hacker` becomes a real link to `http://evil.com`. If `<script>...</script>` is inserted, that becomes XSS — script executes in the page context.

---

### ⚠️ Why it's dangerous

- Modify site appearance (insert text, images, buttons).  
- Phishing — inject malicious links or fake login prompts.  
- XSS — execute scripts in victim's browser (steal cookies, session tokens, perform actions).

---

### 🧰 How to prevent (essentials)

**Never trust user input.**

1. **Sanitize input** — remove or filter HTML tags before rendering. Example:
   `function sanitize(input) { return input.replace(/<[^>]*>/g, ""); }`

2. **Encode output** — convert special characters: `<` → `&lt;`, `>` → `&gt;`, `"` → `&quot;`, `'` → `&#39;`.

3. **Safe output methods** — use `textContent` instead of `innerHTML` in the browser:  
   `element.textContent = userInput; // safe`

4. **Use templating engines with auto-escaping** — server-side templates like Django, Jinja2, EJS usually escape by default.

5. **Whitelist allowed tags/attrs** — if supporting limited HTML, enforce a whitelist.

---

### 🧩 Difference from SQL Injection

| Characteristic   | HTML Injection                    | SQL Injection                        |
| ---------------- | --------------------------------- | ------------------------------------ |
| Where it happens | Client-side (browser)             | Server-side (database)               |
| What it changes  | Page appearance / behavior        | Database queries / stored data       |
| Goal             | Interface manipulation / phishing | Data theft/modification, auth bypass |
| Attack type      | Visual / XSS                      | Injection / server-side              |

---

### 🧠 Summary

- **Definition:** Injecting HTML into a page via user input.  
- **Cause:** Lack of sanitization/encoding.  
- **Consequences:** UI changes, phishing, XSS, client-side data theft.  
- **Mitigation:** Encoding, sanitization, safe output methods, templating engines.

**Analogy:** letting a user write directly into your HTML is like giving them the power to redesign your site.

**Key takeaway:** HTML injection is a compromise of the browser's trust — always validate and escape user input, even for simple fields like "name".
