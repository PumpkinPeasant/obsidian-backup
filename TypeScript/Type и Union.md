## 1. Общие возможности

Оба позволяют описывать форму объекта:
```ts
type UserType = {
  id: number;
  name: string;
};

interface UserInterface {
  id: number;
  name: string;
}
```

## 2. Расширение (extends)

- `interface` поддерживает наследование через `extends`
- `type` расширяется через `&` (intersection)

```ts
interface Admin extends UserInterface {
  role: string;
}

type AdminType = UserType & { role: string };
```

## 3. Поведение при объединении

- `interface` можно **дополнять** (declaration merging)
    
- `type` так не умеет
    

```ts
interface User {
  id: number;
}
interface User {
  name: string;
}
// = { id: number; name: string; }
```

```ts
type User = { id: number };
// ❌ Нельзя повторно объявить type с тем же именем
```

## 4. Типы примитивов, union и tuple

- `type` может описывать примитивы, объединения, кортежи
    
- `interface` только объекты и классы
    

```ts
type ID = string | number; // ✅
type Point = [number, number]; // ✅

interface ID { } // ❌ нельзя
```

## 5. Использование с классами

Оба можно имплементировать:

```ts
interface Person {
  name: string;
}
class User implements Person {
  constructor(public name: string) {}
}
```

## 6. Рекомендации

- `interface` — когда описываешь **структуру объекта или контракт класса**
    
- `type` — когда нужны **union, примитивы, кортежи** или алиасы
    

---

🔑 **Итог:**

- `interface` → расширяемый, декларативный, удобен для объектов/классов
    
- `type` → универсальный, может описывать что угодно (union, tuple, примитивы)
    
- В современных проектах чаще используют **`type` для всего, кроме контрактов классов**, но строгого правила нет
    

```

Хочешь, я сделаю такой же конспект по **Utility Types** (`Partial`, `Pick`, `Omit`, `Required`, `Record`)?
```