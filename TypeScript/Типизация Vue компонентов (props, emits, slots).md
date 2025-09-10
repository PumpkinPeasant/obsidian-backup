## 1. Типизация props

### Вариант с defineProps (Composition API)
```ts
<script setup lang="ts">
interface Props {
  id: number;
  name?: string;
}

const props = defineProps<Props>();
</script>
```

### С литеральным объектом

```ts
<script setup lang="ts">
const props = defineProps<{
  id: number;
  name?: string;
}>();
</script>
```

---

## 2. Типизация emits

### Вариант с defineEmits

```ts
<script setup lang="ts">
const emit = defineEmits<{
  (e: "update", value: string): void;
  (e: "delete", id: number): void;
}>();

function onClick() {
  emit("update", "new value");
  emit("delete", 1);
}
</script>
```

---

## 3. Типизация slots

```ts
<script setup lang="ts">
const slots = defineSlots<{
  default: { msg: string };
  header?: {};
}>();
</script>

<template>
  <slot name="header"></slot>
  <slot :msg="'Hello from child'" />
</template>
```

Использование:

```vue
<Child>
  <template #default="{ msg }">
    <p>{{ msg }}</p>
  </template>
</Child>
```

---

## 4. Типизация компонентов в Options API

```ts
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    id: { type: Number, required: true },
    name: { type: String, required: false }
  },
  emits: ["update", "delete"],
  setup(props, { emit, slots }) {
    emit("update", "value");
    emit("delete", 1);
    return () => slots.default?.();
  }
});
```

---

## 5. Вспомогательные типы

```ts
import type { PropType } from "vue";

const props = defineProps<{
  items: string[];
  config: {
    readonly theme: "dark" | "light";
    options?: number[];
  };
  callback: PropType<(value: string) => void>;
}>();
```

---

🔑 **Итог:**

- `defineProps<T>()` → типизация входных параметров
- `defineEmits<T>()` → типизация событий
- `defineSlots<T>()` → строгая типизация слотов
- В Options API → используем `props`, `emits` с `defineComponent`
- Для сложных случаев → `PropType<T>`