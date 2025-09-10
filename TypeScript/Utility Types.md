## 1. Partial< T >
Делает все поля **необязательными**.

```ts
interface User {
  id: number;
  name: string;
  age: number;
}

type PartialUser = Partial<User>;
/*
{
  id?: number;
  name?: string;
  age?: number;
}
*/
```

---

## 2. Required

Делает все поля **обязательными** (обратное к `Partial`).

```ts
interface User {
  id?: number;
  name?: string;
}

type RequiredUser = Required<User>;
/*
{
  id: number;
  name: string;
}
*/
```

---

## 3. Pick<T, K>

Выбирает только указанные ключи.

```ts
interface User {
  id: number;
  name: string;
  age: number;
}

type UserPreview = Pick<User, "id" | "name">;
/*
{
  id: number;
  name: string;
}
*/
```

---

## 4. Omit<T, K>

Удаляет указанные ключи (обратное к `Pick`).

```ts
interface User {
  id: number;
  name: string;
  age: number;
}

type UserWithoutAge = Omit<User, "age">;
/*
{
  id: number;
  name: string;
}
*/
```

---

## 5. Record<K, T>

Создаёт объект, у которого ключи имеют тип `K`, а значения — тип `T`.

```ts
type Roles = "admin" | "user" | "guest";

type RolePermissions = Record<Roles, boolean>;
/*
{
  admin: boolean;
  user: boolean;
  guest: boolean;
}
*/

const permissions: RolePermissions = {
  admin: true,
  user: false,
  guest: false
};
```

---

🔑 **Итог:**

- `Partial<T>` — все поля необязательные
- `Required<T>` — все поля обязательные
- `Pick<T, K>` — выбрать только нужные ключи
- `Omit<T, K>` — исключить ненужные ключи
- `Record<K, T>` — объект-словарь с ключами `K` и значениями `T`