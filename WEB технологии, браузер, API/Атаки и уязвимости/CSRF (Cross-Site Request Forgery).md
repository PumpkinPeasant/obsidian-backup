## 1. Что такое CSRF
- Уязвимость, при которой злоумышленник заставляет **авторизованного пользователя** выполнить запрос на сайт без его ведома.  
- Опасно, если на сайте используются cookies для аутентификации.  
- Пример атаки:
```html
<form action="https://bank.com/transfer" method="POST">
  <input type="hidden" name="to" value="attacker">
  <input type="hidden" name="amount" value="1000">
</form>
<script>document.forms[0].submit()</script>
```

👉 Если у пользователя есть сессия (cookie), запрос выполнится от его имени.

---

## 2. Как защититься

### SameSite Cookies

- Ограничиваем отправку cookies при кросс-доменных запросах.

Пример:
```http
Set-Cookie: sessionId=abc123; HttpOnly; Secure; SameSite=Strict
```

- `Strict` → куки отправляются только внутри одного домена.
- `Lax` → разрешает куки при переходах по ссылке (GET).
- `None` → всегда отправляются (только с `Secure`).

---

### CSRF-токены

- Сервер выдаёт уникальный токен при загрузке страницы/формы.
- Клиент отправляет его вместе с запросом.
- Сервер проверяет совпадение токена.  

Пример:
```html
<input type="hidden" name="csrf_token" value="xyz123">
```

---

### Проверка Origin / Referer

- Сервер проверяет заголовки:

```http
Origin: https://trusted.com
Referer: https://trusted.com/page
```

👉 Если заголовок от другого домена → отклонить запрос.

---

## 3. Практические советы

- Для всех cookies сессии → `HttpOnly; Secure; SameSite=Lax/Strict`.
- Реализовать CSRF-токены для POST/PUT/DELETE-запросов.
- Проверять `Origin` и `Referer` на сервере.
- Использовать `double submit cookie` (CSRF-токен дублируется и в cookie, и в теле запроса).

---

🔑 **Итог:**  
CSRF = подделка запроса от лица пользователя.  
Защита:
- `SameSite` cookies;
- CSRF-токены;
- проверка `Origin` и `Referer`.
