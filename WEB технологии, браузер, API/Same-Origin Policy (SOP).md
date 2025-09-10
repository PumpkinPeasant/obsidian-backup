## 1. Что такое Same-Origin Policy
- **Политика одного источника (SOP)** — механизм безопасности браузеров.  
- Ограничивает доступ скриптов с одного origin к ресурсам другого origin.  
- Origin = **схема (протокол) + домен + порт**  

Пример:
- https://example.com/page → origin = `https://example.com:443`  
- http://example.com → ❌ другой протокол  
- https://sub.example.com → ❌ другой домен  
- https://example.com:8080 → ❌ другой порт  

---

## 2. Что ограничивается
- Чтение данных с другого origin:  
  - `XMLHttpRequest` / `fetch`  
  - доступ к `localStorage`, `sessionStorage`  
  - доступ к DOM другого окна (iframe, popup)  

---

## 3. Что разрешено
- Загрузка ресурсов (картинок, скриптов, стилей) **разрешена без ограничений**:
  ```html
  <img src="https://other.com/logo.png" />
  <script src="https://cdn.com/lib.js"></script>
```

- Но скрипт из другого origin **не сможет читать** содержимое ответа без CORS.

---

## 4. Пример блокировки

```ts
fetch("https://api.other.com/data")
  .then(r => r.json())
  .catch(err => console.error(err));
```

👉 Если сервер не вернёт CORS-заголовок (`Access-Control-Allow-Origin`), браузер заблокирует доступ.

---

## 5. Взаимодействие с iframe

- Доступ к `window.frames` разрешён,
- но доступ к **DOM внутри iframe** → только если origin совпадает.

---

## 6. Как обойти ограничения

- Сервер должен настроить **CORS** и явно разрешить доступ.
- Либо использовать **прокси** (запрос к backend → backend сам запрашивает данные → возвращает клиенту).

---

🔑 **Итог:**
- Same-Origin Policy защищает пользователя от XSS и CSRF
- Origin = протокол + домен + порт
- Запрещает доступ JS к чужим данным без разрешения
- Обход возможен через CORS или backend-прокси