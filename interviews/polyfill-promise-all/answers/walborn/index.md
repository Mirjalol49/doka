---
excluded:
  - js/promise
---

### Теория

Для начала вспомним работу оригинального `Promise.all`.

Он принимает коллекцию промисов, начинает одновременно их выполнять и возвращает новый промис. Если все переданные промисы выполнятся, возвращаемый промис тоже выполнится и в нём будет лежать массив результатов, причём в том же порядке. Но! Если какой-то промис вылетел с ошибкой, то `Promise.all` прекращает работу раньше и возвращаемый промис будет отклонён.

Таким образом у нас есть два сценария:

- Позитивный: Когда все промисы завершились успешно. Тут в ответ придёт массив результатов с сохранением очерёдности.
- Негативный: Когда какой-то промис завершился с ошибкой. Тут `Promise.all` не будет ждать завершение оставшихся, а сразу перейдёт в состояние `rejected` с полученной ошибкой.

### Подсказки

Сначала попробуйте решить самостоятельно. Но если не получается, то вот подсказки:

1. Где-то нужно хранить результаты и как-то отслеживать, что все промисы завершились.
1. Возвращаться должен тоже промис.
1. По завершению каждого промиса не забываем:
  - запомнить результат под правильным индексом
  - отметить, что активных промисов стало меньше на один
1. Случай, когда у нас произошла ошибка, обрабатывать отдельно не нужно — возвращаемый промис автоматически перейдёт в состояние `rejected`.

### Решение

Напишем код и прокомментируем каждую строчку

```jsx
// На вход к нам приходит массив промисов
Promise.all = (promises) => {
  // Здесь будем хранить результаты успешно завершенных промисов
  const results = []

  // Количество промисов, которые осталось выполнить
  // На данный момент не выполнился еще ни один промис!
  let rest = promises.length

  // Возвращаем, естественно, новый промис
  return new Promise((resolve) => {
    // Проходимся по списочку
    promises.forEach((promise, index) => {
      promise
        // Если промис завершается успешно
        .then((result) => {

          // Кладём его в наше хранилище
          // Причём сохраняем индекс, под которым он был в массиве `promises`
          results[index] = result

          // На один невыполненный промис стало меньше!
          rest -= 1

          // Если активных промисов больше нет, то резолвим результат
          if (rest === 0) resolve(results)
        })
    })
  })
}
```

### Тесты

Теперь протестируем наш полифил

```jsx
// Сделаем искусственную задержку
const delay = (timeout) => new Promise((resolve) => setTimeout(resolve, timeout))

// И создадим несколько промисов для тестирования
const fetchUsers = () => delay(1000).then(() => [ 'Маша', 'Петя', 'Оля' ])
const problemPromise = delay(2000).then(() => { throw 'Houston, we have a problem' })
const stringPromise = delay(5000).then(() => 'Lorem ipsum dolor sit amet')

// Прогоним позитивный случай
Promise
  .all([ fetchUsers(), stringPromise ])
  .then(console.log)
/*
[
  [ 'Маша', 'Петя', 'Оля' ],
  'Lorem ipsum dolor sit amet'
]
*/

// Прогоним негативный случай, когда возникает ошибка
Promise
  .all([ fetchUsers(), problemPromise, stringPromise ])
  .then(console.log)
/*
Uncaught (in promise) Houston, we have a problem
*/
```
