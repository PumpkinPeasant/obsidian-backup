Proxy - это объект-обертка, который позволяет который **перехватывает любые обращения к полям**. 

Proxy переопределяет базовые действия, такие как получение (`Get`) и установка (`Set`) свойств.

Прокси-объекты обычно используются для регистрации обращений к свойствам, проверки, форматирования или очистки входных данных и т.д.
#### Базовый пример

``` js
const user = {
  name: "Alex",
  age: 25
};

const proxy = new Proxy(user, {
  get(target, prop) {
    console.log(`Читаем свойство: ${prop}`);
    return target[prop];
  },

  set(target, prop, value) {
    console.log(`Записываем ${prop} = ${value}`);
    target[prop] = value;
    return true;
  }
});
```
#### Создание прокси

Proxy создается с двумя параметрами:

- `target`: ссылка на оригинальный объект, который будет обернут в Proxy;

- `handler`: объект, который определяет, какие операции будут перехвачены и как переопределить перехваченные операции.

``` js
const target = {
  message1: "hello",
  message2: "everyone",
};

const handler2 = {
  get(target, prop) {
    return target[prop];
  },
  
  set(target, prop, value){
   target[prop] = value;
  }
};

const proxy2 = new Proxy(target, handler2);
```

[`get()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/Proxy/get) перехватывает попытки доступа к свойствам оригинального объекта. 
	- `target`: ссылка на оригинальный объект;
	- `prop`: поле оригинального объекта, к которому происходит попытка доступа;

`set()` перехватывает попытки доступа к свойствам оригинального объекта. 

**Set** **должен возвращать `true` или `false`**
По спецификации `set` **обязан** вернуть `boolean`. Если вернуть `false` — в strict mode будет выброшена ошибка.