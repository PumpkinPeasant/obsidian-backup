**`Object.defineProperty()`** - это статический метод, который напрямую определяет новое свойство объекта или изменяет существующее свойство и возвращает этот объект.
 
 ``` js
const object = {};

Object.defineProperty(object, "foo", {
  value: 42,
  writable: false,
});

object.foo = 77;
// Throws an error in strict mode

console.log(object.foo);
// Expected output: 42

 ```

