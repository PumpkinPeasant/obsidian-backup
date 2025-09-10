## 1. Enum (перечисления)

### Numeric enum
По умолчанию значения — числа (начиная с `0`).
```ts
enum Direction {
  Up,       // 0
  Down,     // 1
  Left,     // 2
  Right     // 3
}

let dir: Direction = Direction.Left; // 2
```

### String enum

Можно задавать строковые значения.

```ts
enum Role {
  Admin = "admin",
  User = "user",
  Guest = "guest"
}

let r: Role = Role.Admin; // "admin"
```

### Преимущества enum

- Удобно ограничивать набор значений
- Легко использовать в `switch/case`
- Можно обращаться по значению и по имени (для числовых enum)

---

## 2. `as const`

Позволяет сделать объект/массив:

- **readonly** (нельзя изменить)
- значения — **литеральными**, а не просто `string`/`number`

```ts
const roles = ["admin", "user", "guest"] as const;
// Тип: readonly ["admin", "user", "guest"]

type Role = typeof roles[number];
// Тип: "admin" | "user" | "guest"
```

### Пример с объектом

```ts
const COLORS = {
  RED: "red",
  BLUE: "blue",
  GREEN: "green"
} as const;

// Тип: { readonly RED: "red"; readonly BLUE: "blue"; readonly GREEN: "green" }

type Color = typeof COLORS[keyof typeof COLORS];
// Тип: "red" | "blue" | "green"
```

---

## 3. Enum vs `as const`

|Enum|as const|
|---|---|
|Генерируется в JS-код|Только типовая конструкция (нет кода)|
|Поддержка обратного маппинга|Нет|
|Удобно для switch-case|Легче и современнее|
|Может быть `number` или `string`|Обычно строковые литералы|

---

🔑 **Итог:**
- **Enum** → когда нужен «живой» объект в JS (часто в legacy или C#-подобном стиле).
- **`as const`** → современный способ, лёгкий и безопасный, даёт union-тип значений.