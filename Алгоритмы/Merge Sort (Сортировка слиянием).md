**Merge Sort** (Сортировка слиянием) — это один из самых эффективных алгоритмов сортировки. Он работает по принципу "**разделяй и властвуй**" (divide and conquer). Его главная особенность в том, что он постоянно делит задачу на более мелкие, а потом решает их и объединяет.

---

### Как работает алгоритм?

Алгоритм состоит из двух основных этапов:

1. **Разделение (Splitting):** Мы начинаем с исходного массива и **рекурсивно делим его пополам**. Этот процесс продолжается до тех пор, пока мы не получим множество массивов, каждый из которых содержит **всего один элемент**. Массив из одного элемента по определению считается отсортированным.
    
2. **Слияние (Merging):** После разделения начинается обратный процесс. Мы **объединяем эти единичные массивы попарно**, но делаем это так, чтобы новый объединенный массив всегда был отсортирован. Мы используем **указатели**, чтобы сравнивать первые элементы из каждого массива и добавлять меньший в новый объединенный массив. Этот процесс повторяется, пока все элементы не будут слиты в один большой, полностью отсортированный массив.

---

### Сложность алгоритма

- **Временная сложность:** O(n log n)
    - Время, которое уходит на разделение, составляет O(log n). А время, которое уходит на слияние, составляет O(n), потому что нам нужно пройти по всем элементам. Если мы объединим эти два показателя, то получим O(n log n). 
    
- **Пространственная сложность (память):** O(n)
    - Merge Sort требует дополнительной памяти, чтобы хранить временные массивы во время процесса слияния. В худшем случае, нам потребуется память, равная размеру исходного массива.

### Код на TypeScript

```ts
function mergeSort(arr: number[]): number[] {
  // Базовый случай: если массив состоит из одного элемента или пустой, просто возвращаем его
  if (arr.length <= 1) {
    return arr;
  }

  // 1. Разделение
  const middle = Math.floor(arr.length / 2);
  const left: number[] = arr.slice(0, middle);
  const right: number[] = arr.slice(middle);

  // Рекурсивно вызываем mergeSort для левой и правой половин
  const sortedLeft = mergeSort(left);
  const sortedRight = mergeSort(right);

  // 2. Слияние (возвращаем результат слияния)
  let mergerArr: number[] = [];
  let leftPointer = 0;
  let rightPointer = 0;

  // Главный цикл слияния
  while (leftPointer < sortedLeft.length && rightPointer < sortedRight.length) {
    if (sortedLeft[leftPointer] < sortedRight[rightPointer]) {
      mergerArr.push(sortedLeft[leftPointer]);
      leftPointer++;
    } else {
      mergerArr.push(sortedRight[rightPointer]);
      rightPointer++;
    }
  }

  // Добавляем оставшиеся элементы, если они есть
  while (leftPointer < sortedLeft.length) {
    mergerArr.push(sortedLeft[leftPointer]);
    leftPointer++;
  }

  while (rightPointer < sortedRight.length) {
    mergerArr.push(sortedRight[rightPointer]);
    rightPointer++;
  }

  return mergerArr;
}

// Пример использования
const unsortedArray = [8, 3, 1, 7, 0, 10, 2];
const sortedArray = mergeSort(unsortedArray);
console.log(sortedArray); // Выведет [0, 1, 2, 3, 7, 8, 10]
```

