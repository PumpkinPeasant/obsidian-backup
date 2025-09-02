
- **`Promise.all([p1, p2, ...])`**
    - Ждёт выполнения **всех промисов**.
    - Если хотя бы один завершится с ошибкой → весь `Promise.all` перейдёт в `rejected`.
    - Возвращает массив результатов в том же порядке, что и исходный массив.
    
    `Promise.all([fetchUser(), fetchPosts()])   .then(([user, posts]) => console.log(user, posts))   .catch(err => console.error("Ошибка:", err));`
    
- **`Promise.allSettled([p1, p2, ...])`**
    - Ждёт выполнения всех промисов.
    - Никогда не падает — возвращает массив объектов `{status: "fulfilled" | "rejected", value | reason}`.
    
    `Promise.allSettled([fetchUser(), fetchBroken()])   .then(results => console.log(results));`
    
- **`Promise.race([p1, p2, ...])`**
    - Возвращает результат **первого завершившегося промиса** (успех или ошибка).
    
    `Promise.race([fetchFast(), fetchSlow()])   .then(res => console.log("Первый:", res))   .catch(err => console.error("Ошибка:", err));`
    
- **`Promise.any([p1, p2, ...])`** (ES2021)
    - Возвращает **первый успешно выполненный промис**.
    - Если все завершились с ошибкой → выбросит **AggregateError**.
    
    `Promise.any([fetchFail(), fetchUser()])   .then(res => console.log("Успех:", res))   .catch(err => console.error("Все упали:", err));`


### Promise

```ts
interface Account {
  name: string;
  balance: number;
}

const accounts: Account[] = [
  { name: "Alice", balance: 500 },
  { name: "Bob", balance: 300 },
  { name: "Charlie", balance: 1000 },
];

 const withdraw = (accountName: string, amount: number): Promise<string | Error> => {
    return new Promise((resolve,reject)=>{    
        console.log('Please wait...')
        setTimeout(()=>{
            let account = accounts.find(account => account.name === accountName)
            if(!account) reject(new Error('Account not found'))
            if(account.balance < amount) reject(new Error('Not enough money'))
            account.balance-= amount
            resolve(`Your current balance is: ${account.balance}`)
        }, 1000)
    })
}

console.log('ATM is ready to work')

withdraw('Alice', 500).then(result => console.log(result)).catch(err => console.error(err));
```
### Promise.all: возвращает значения всех промисов, если они завершились успешно
Метод `Promise.all()` возвращает массив значений всех переданных промисов, при этом сохраняя порядок оригинального (переданного) массива, но не порядок выполнения. 
Если хотя бы один промис из переданного массива завершится с ошибкой, то `Promise.all()`тоже завершится с этой ошибкой.
``` ts
interface Todo {
    userId: number;
    id: number;
    title: string;
    completed: boolean;
} 

const todoIds: Number[] = [1,2,3]
let todoPromises: Promise<Todo>[] = []

todoIds.forEach(id => {
    const promise = fetch(`https://jsonplaceholder.typicode.com/todos/${id}`).then(response => {
            if (!response.ok) {
                throw new Error("Ошибка сети: " + response.status);
            }
            return response.json();
        })
        .then((data: Todo) => data);
    todoPromises.push(promise)    
})

Promise.all(todoPromises)
  .then((responses) => {
    responses.forEach(res => console.log(res.title))
  })
  .catch(err => console.error(err));
```

### Promise.any: возвращает значение первого успешно выполнившегося промиса
В отличие от `Promise.all()`, который содержит массив значений исполненных промисов, `Promise.any()` содержит только одно значение при условии, что хотя бы один из промисов исполнен успешно.
```ts
interface Courier {
  name: string;
  time: number;
  lostOrder: boolean;
}

const couriers: Courier[] = [
  { name: "Камил", time: 2000, lostOrder: false },
  { name: "Бабиджон", time: 1000, lostOrder: false },
  { name: "Мурад", time: 1500, lostOrder: true },
];

const orderedDeliveries = couriers.map(courier => {
  return new Promise<string>((resolve, reject) => {
    setTimeout(() => {
      if (courier.lostOrder) reject(new Error(`Курьер ${courier.name} потерял ваш заказ :(`));
      else resolve(`Курьер ${courier.name} доставил ваш заказ за ${courier.time / 100} минут`);
    }, courier.time);
  });
});

Promise.any(orderedDeliveries)
  .then(result => console.log(result))
  .catch(() => console.log("Вы остались голодными"));
```