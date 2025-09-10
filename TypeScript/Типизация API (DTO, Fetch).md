## 1. DTO (Data Transfer Object)
Описываем структуру данных, которые приходят или уходят в API.

```ts
// DTO для пользователя
interface UserDTO {
  id: number;
  name: string;
  email: string;
}
```

---

## 2. Типизация fetch

### Базовый вариант

```ts
async function getUser(id: number): Promise<UserDTO> {
  const response = await fetch(`/api/users/${id}`);
  if (!response.ok) {
    throw new Error("Network error");
  }
  return response.json();
}
```

---

## 3. Обёртка с Generics

Чтобы переиспользовать типизацию для разных запросов:

```ts
async function apiFetch<T>(url: string): Promise<T> {
  const response = await fetch(url);
  if (!response.ok) throw new Error("Network error");
  return response.json() as Promise<T>;
}

// Использование
const user = await apiFetch<UserDTO>("/api/users/1");
```

---

## 4. Ответы с мета-данными

Часто API возвращает не только данные, но и статус/сообщение.

```ts
interface ApiResponse<T> {
  data: T;
  success: boolean;
  error?: string;
}

async function api<T>(url: string): Promise<ApiResponse<T>> {
  const res = await fetch(url);
  return res.json();
}

type UsersResponse = ApiResponse<UserDTO[]>;

const users = await api<UserDTO[]>("/api/users");
```

---

## 5. Пример типизации POST-запроса

```ts
interface CreateUserDTO {
  name: string;
  email: string;
}

async function createUser(user: CreateUserDTO): Promise<UserDTO> {
  const res = await fetch("/api/users", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(user),
  });

  return res.json();
}
```

---

## 6. Практические советы

- DTO описываем **отдельными интерфейсами** или `type`
- Для сложных API удобно делать `ApiResponse<T>`
- `Generics` позволяют писать универсальные API-обёртки
- Лучше использовать **`as const`** для фиксированных значений (например, статус-коды, роли)

---

🔑 **Итог:**

- DTO → описание структуры данных
- `fetch<T>` → типизируем ответ
- Обёртки с Generics → переиспользуем код
- Универсальный паттерн → `ApiResponse<T>`
