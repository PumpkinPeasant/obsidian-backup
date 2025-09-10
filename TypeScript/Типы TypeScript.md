## 1. string

Строки, как в JS.
```ts
let name: string = "Alice";
```

## 2. number

Все числа (целые, дробные, отрицательные, `NaN`, `Infinity`).

```ts
let age: number = 25;
let price: number = 19.99;
```

## 3. boolean

Логические значения: `true` или `false`.

```ts
let isAdmin: boolean = false;
```

## 4. null

Явное отсутствие значения.

```ts
let data: null = null;
```

## 5. undefined

Значение «не присвоено».

```ts
let x: undefined = undefined;
```

Обычно используют вместе в `union`:

```ts
let value: string | null | undefined;
```

## 6. void

Используется для функций, которые **ничего не возвращают**.

```ts
function log(message: string): void {
  console.log(message);
}
```

## 7. any

Отключает проверку типов. Можно присвоить что угодно.  
⚠️ **Опасно — сводит пользу TypeScript к нулю.**

```ts
let data: any = 42;
data = "hello";
data = { foo: "bar" };
```

## 8. unknown

Аналог `any`, но **безопасный**: требует проверку перед использованием.

```ts
let input: unknown;

input = "text";
input = 123;

// Ошибка: нельзя вызвать методы без проверки
// console.log(input.toFixed(2));

if (typeof input === "number") {
  console.log(input.toFixed(2)); // ✅ теперь можно
}
```

## 9. never

Тип, который **никогда не имеет значения**. Используется:

- для функций, которые не завершаются (ошибка, бесконечный цикл)
- для случаев, которые «не могут произойти»

```ts
function fail(message: string): never {
  throw new Error(message);
}

function infiniteLoop(): never {
  while (true) {}
}
```

---

🔑 **Итог:**

- `string`, `number`, `boolean` — основные примитивы
- `null` и `undefined` — отсутствие значения
- `void` — «ничего не возвращает»
- `any` — небезопасный «любой тип»
- `unknown` — безопасный аналог `any` (надо проверять)
- `never` — «невозможный тип»