**Директивы во Vue** — это специальные атрибуты с префиксом `v-`, которые добавляют элементам особое поведение.

### 🔹 Основные встроенные директивы:

- `v-bind` → связывает атрибут с реактивным значением.
    
    `<img v-bind:src="imageUrl" /> <!-- сокращённая форма --> <img :src="imageUrl" />`
    
- `v-model` → двустороннее связывание данных (input ↔ data).
    
    `<input v-model="name" />`
    
- `v-if`, `v-else-if`, `v-else` → условный рендеринг.
    
    `<p v-if="isAdmin">Админ</p> <p v-else>Пользователь</p>`
    
- `v-show` → условное отображение (не удаляет элемент, а ставит `display: none`).
    
    `<p v-show="visible">Видимый текст</p>`
    
- `v-for` → цикл по массиву или объекту.
    
    `<li v-for="user in users" :key="user.id">{{ user.name }}</li>`
    
- `v-on` → слушатель событий.
    
    `<button v-on:click="increment">+</button> <!-- сокращённая форма --> <button @click="increment">+</button>`