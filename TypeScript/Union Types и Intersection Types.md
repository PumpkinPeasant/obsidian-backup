## 1. Union Types (объединение, ИЛИ)
Позволяют задать несколько возможных типов (`A | B`).

```ts
let id: string | number;

id = "abc";  // ✅
id = 123;    // ✅
id = true;   // ❌
```

### Пример с функцией

```ts
function printId(id: string | number) {
  if (typeof id === "string") {
    console.log("ID in uppercase:", id.toUpperCase());
  } else {
    console.log("ID + 1:", id + 1);
  }
}
```

### Пример с типами

```ts
type Dog = { bark: () => void };
type Cat = { meow: () => void };

type Pet = Dog | Cat;

function play(pet: Pet) {
  // Нужно сужать тип
  if ("bark" in pet) pet.bark();
  if ("meow" in pet) pet.meow();
}
```

---

## 2. Intersection Types (пересечение, И)

Объединяют несколько типов в один (`A & B`). Объект должен соответствовать **всем** типам сразу.

```ts
type HasId = { id: number };
type HasName = { name: string };

type User = HasId & HasName;

const u: User = { id: 1, name: "Alice" }; // ✅
```

### Пример с классами

```ts
type Timestamps = { createdAt: Date; updatedAt: Date };
type Entity = { id: number; name: string };

type Model = Entity & Timestamps;

const product: Model = {
  id: 42,
  name: "Book",
  createdAt: new Date(),
  updatedAt: new Date(),
};
```

---

## 3. Сравнение

- **Union (`|`)** → один из вариантов
- **Intersection (`&`)** → все варианты сразу

```ts
type A = { foo: string };
type B = { bar: number };

type U = A | B; // объект может быть как A, так и B
type I = A & B; // объект обязан быть и A, и B
```

---

🔑 **Итог:**

- Union = «или» → выбор одного типа из нескольких
- Intersection = «и» → объединение нескольких типов в один
- Часто используют вместе для гибкой типизации
