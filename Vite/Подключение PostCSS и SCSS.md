## 1. Подключение SCSS
Vite поддерживает SCSS "из коробки" (если установлен `sass`).
### Установка
```bash
npm install -D sass
```

### Использование

В компоненте Vue или любом `.ts`/`.js` файле:

```vue
<style lang="scss">
$primary: #42b883;

.button {
  background: $primary;
}
</style>
```

---

## 2. Подключение глобальных SCSS-переменных

Чтобы не импортировать переменные в каждом файле, можно использовать `additionalData`:

`vite.config.ts`:

```ts
import { defineConfig } from "vite";
import vue from "@vitejs/plugin-vue";

export default defineConfig({
  plugins: [vue()],
  css: {
    preprocessorOptions: {
      scss: {
        additionalData: `@import "@/styles/variables.scss";`
      }
    }
  }
});
```

Теперь переменные доступны во всех SCSS-файлах.

---

## 3. Подключение PostCSS

Vite автоматически ищет конфиг в:

- `postcss.config.js`
- `postcss.config.cjs`
- `vite.config.ts` (через `css.postcss`)

### Установка

```bash
npm install -D postcss autoprefixer
```

### Конфигурация

`postcss.config.js`:

```js
module.exports = {
  plugins: {
    autoprefixer: {}
  }
}
```

---

## 4. Использование PostCSS в Vite

`vite.config.ts`:

```ts
export default defineConfig({
  css: {
    postcss: './postcss.config.js'
  }
});
```

---

## 5. Пример: SCSS + PostCSS вместе

- SCSS для переменных и вложенности
    
- PostCSS (autoprefixer) для кроссбраузерности
    

```scss
.button {
  display: flex;
  user-select: none; // autoprefixer добавит -webkit-user-select
}
```

---

🔑 **Итог:**

- SCSS работает в Vite сразу после установки `sass`
- Для глобальных переменных → `css.preprocessorOptions.scss.additionalData`
- PostCSS подключается через `postcss.config.js`
- Часто используют `autoprefixer`, `cssnano`, `postcss-nesting`