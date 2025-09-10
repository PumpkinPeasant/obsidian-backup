## 1. Зачем нужен CORS
- По умолчанию браузер запрещает запросы из одного источника (origin) к другому.  
- **Same-Origin Policy (SOP):** домен, протокол и порт должны совпадать.  
- CORS позволяет **разрешить доступ** к ресурсам с другого origin.  

Пример:
- Frontend: https://app.example.com  
- Backend: https://api.example.com  
👉 Без CORS браузер заблокирует запрос.  

---

## 2. Как работает CORS
Когда браузер делает cross-origin запрос, сервер должен явно указать, что он разрешён.  

Заголовок ответа:
```http
Access-Control-Allow-Origin: https://app.example.com
```

Можно разрешить всем:

```http
Access-Control-Allow-Origin: *
```

---

## 3. Preflight-запросы (OPTIONS)

Для "опасных" запросов (например, с `PUT`, `DELETE`, или нестандартными заголовками) браузер сначала отправляет **предварительный запрос** (`OPTIONS`).

Пример preflight:

```http
OPTIONS /users HTTP/1.1
Origin: https://app.example.com
Access-Control-Request-Method: DELETE
Access-Control-Request-Headers: Content-Type
```

Ответ сервера:

```http
HTTP/1.1 204 No Content
Access-Control-Allow-Origin: https://app.example.com
Access-Control-Allow-Methods: GET, POST, DELETE
Access-Control-Allow-Headers: Content-Type
```

---

## 4. Основные заголовки CORS

- `Access-Control-Allow-Origin` → разрешённые источники
- `Access-Control-Allow-Methods` → методы (`GET, POST, PUT...`)
- `Access-Control-Allow-Headers` → разрешённые заголовки
- `Access-Control-Allow-Credentials: true` → разрешить cookies/Authorization
- `Access-Control-Expose-Headers` → заголовки, доступные в JS

---

## 5. Когда preflight не нужен

- Простые GET/POST-запросы **без нестандартных заголовков** и с типом `Content-Type: application/x-www-form-urlencoded`, `multipart/form-data` или `text/plain`.

---

🔑 **Итог:**

- CORS решает проблему ограничений SOP
- Сервер должен явно разрешать доступ (заголовками)
- Preflight (`OPTIONS`) используется для «опасных» запросов
- Основные заголовки: `Allow-Origin`, `Allow-Methods`, `Allow-Headers`, `Allow-Credentials`