## 1. Базовая структура
Файл: `vite.config.ts`  
```ts
import { defineConfig } from "vite";
import vue from "@vitejs/plugin-vue";

export default defineConfig({
  plugins: [vue()],
});
```

---

## 2. Алиасы

Позволяют указывать короткие пути к файлам.

```ts
import { defineConfig } from "vite";
import path from "path";

export default defineConfig({
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
});
```

Использование:

```ts
import MyComponent from "@/components/MyComponent.vue";
```

---

## 3. Настройка сервера

```ts
export default defineConfig({
  server: {
    port: 3000,
    open: true,         // авто-открытие в браузере
    proxy: {
      "/api": "http://localhost:5000",
    },
  },
});
```

---

## 4. Сборка (build)

```ts
export default defineConfig({
  build: {
    outDir: "dist",          // папка сборки
    sourcemap: true,         // генерация sourcemap
    minify: "esbuild",       // "esbuild" или "terser"
    rollupOptions: {
      output: {
        manualChunks: {      // разделение бандла
          vendor: ["vue"],
        },
      },
    },
  },
});
```

---

## 5. Оптимизация зависимостей

```ts
export default defineConfig({
  optimizeDeps: {
    include: ["lodash", "axios"], // принудительное включение в pre-bundling
    exclude: ["big-lib"],         // исключение из оптимизации
  },
});
```

---

## 6. Env переменные

- Переменные окружения хранятся в `.env` файлах
- Доступ через `import.meta.env`

```ts
export default defineConfig({
  define: {
    __APP_VERSION__: JSON.stringify("1.0.0"),
  },
});
```

---

🔑 **Итог:**  
В `vite.config.ts` можно настроить:

- **plugins** (Vue, React и др.)
- **alias** для путей
- **server** (порт, прокси, авто-открытие)
- **build** (директория, sourcemap, splitChunks)
- **optimizeDeps** (какие пакеты бандлить заранее)
- **env-переменные** через `import.meta.env`