## 1. Что такое Vitest
- Современный тест-раннер для JavaScript/TypeScript  
- Разработан командой Vite  
- Лёгкий и быстрый (использует Vite под капотом для сборки)  
- Поддерживает TS, JSX, Vue, React, Svelte "из коробки"  
- Совместим с синтаксисом Jest (`describe`, `it`, `expect`)  

---
## 2. Установка
```bash
npm install -D vitest
```

В `package.json`:

```json
{
  "scripts": {
    "test": "vitest",
    "test:watch": "vitest --watch"
  }
}
```

---

## 3. Базовое использование

Пример функции:

```ts
export function sum(a: number, b: number) {
  return a + b;
}
```

Тест (`sum.test.ts`):

```ts
import { describe, it, expect } from "vitest";
import { sum } from "./sum";

describe("sum", () => {
  it("складывает числа", () => {
    expect(sum(2, 3)).toBe(5);
  });
});
```

Запуск:

```bash
npm run test
```

---

## 4. Тестирование async-функций

```ts
async function fetchData(): Promise<string> {
  return "data";
}

it("возвращает данные", async () => {
  const result = await fetchData();
  expect(result).toBe("data");
});
```

---

## 5. Моки и шпионы

Vitest поддерживает мокирование и шпионы (аналог Jest).

```ts
import { vi, it, expect } from "vitest";

it("вызывает функцию", () => {
  const fn = vi.fn();
  fn("hello");
  expect(fn).toHaveBeenCalledWith("hello");
});
```

---

## 6. Snapshot-тесты

```ts
import { expect, it } from "vitest";

it("снимок объекта", () => {
  const user = { id: 1, name: "Alice" };
  expect(user).toMatchSnapshot();
});
```

---

## 7. Тестирование Vue-компонентов

С `@vue/test-utils`:

```bash
npm install -D @vue/test-utils
```

```ts
import { mount } from "@vue/test-utils";
import { describe, it, expect } from "vitest";
import Button from "./Button.vue";

describe("Button.vue", () => {
  it("рендерит текст", () => {
    const wrapper = mount(Button, { props: { label: "Click" } });
    expect(wrapper.text()).toBe("Click");
  });
});
```

---

## 8. Преимущества Vitest

- Быстрый запуск благодаря Vite
- Поддержка TypeScript без дополнительной настройки
- Совместим с экосистемой Jest (легко мигрировать)
- Удобен для проектов на Vue, React, Svelte
- Отлично работает в режиме `watch`

---

🔑 **Итог:**  
Vitest — это современная альтернатива Jest, идеально подходящая для проектов на Vite/Vue/TS.  
Он позволяет писать unit, snapshot и даже компонентные тесты быстро и удобно.