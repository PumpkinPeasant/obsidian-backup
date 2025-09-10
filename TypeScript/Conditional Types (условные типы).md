
Conditional Types позволяют описывать тип, который зависит от условия.

---

## 1. Базовый синтаксис

```ts
T extends U ? X : Y
```

- Если `T` совместим с `U`, то берётся `X`
- Иначе берётся `Y`

---

## 2. Пример: проверка типа

```ts
type IsString<T> = T extends string ? "yes" : "no";

type A = IsString<string>;  // "yes"
type B = IsString<number>;  // "no"
```

---

## 3. Использование с дженериками

```ts
function toArray<T>(value: T): T extends any[] ? T : T[] {
  return (Array.isArray(value) ? value : [value]) as any;
}

const a = toArray(5);        // number[]
const b = toArray([1, 2, 3]); // number[]
```

---

## 4. Условие с `keyof`

```ts
type ElementType<T> = T extends (infer U)[] ? U : T;

type A = ElementType<number[]>; // number
type B = ElementType<string>;   // string
```

---

## 5. Условие с union

Conditional Types **распространяются** на каждый элемент union (distributive).

```ts
type ToBoolean<T> = T extends number ? true : false;

type Result = ToBoolean<1 | "a" | 2>; 
// true | false | true
```

---

## 6. Пример: исключение типов

```ts
type Exclude<T, U> = T extends U ? never : T;

type A = Exclude<"a" | "b" | "c", "a" | "c">;
// "b"
```

---

🔑 **Итог:**

- `T extends U ? X : Y` — выбор типа по условию
- Часто используется с дженериками
- Работает распределённо на union-типы
- Применяется в Utility Types (`Exclude`, `Extract`, `NonNullable`)