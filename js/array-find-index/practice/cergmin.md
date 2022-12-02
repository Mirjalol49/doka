#### 🛠 indexOf или findIndex

Помимо `findIndex()`, у массивов есть ещё и метод [`indexOf()`](/js/index-of/). Он работает схожим образом: возвращает индекс первого подходящего элемента или `-1`, но, в отличие от `findIndex()`, принимает как аргумент не функцию-предикат, а искомое значение.

```js
const numbers = [1, 7, 4, 6, 2, 8, 3]

console.log(numbers.indexOf(2))
// 4 (значение 2 хранится по индексу 4)

numbers.findIndex((element) => element === 2)
// 4
```

Кажется, что метод `indexOf()` проще в использовании, и это действительно так, но из-за своей простоты, он уступает методу `findIndex()` в функциональности.

Например, если мы хотим осуществить поиск по массиву объектов, то `indexOf()` вряд ли сможет нам помочь.

```js
const friends = [
  { name: 'Андрей' },
  { name: 'Маша' },
  { name: 'Артём' }
]

// Элемент не найден
console.log(
    friends.indexOf({ name: 'Артём' })
)
// -1

console.log(
  friends.findIndex(
    (element) => element.name === 'Артём'
  )
)
// 2
```

Дело в том, что переменная не хранит в себе содержимое объекта, она содержит только [ссылку на него](/js/ref-type-vs-value-type/#ssylochnye-tipy-dannyh). Следовательно, `indexOf()` сравнивает ссылки, а не сами объекты.

```js
// ссылка на объект 1
let tomato = { color: 'red' }

// ссылка на объект 2
let strawberry = { color: 'red' }
```

Сравнение этих двух объектов вернёт `false` несмотря на то, что значения ключей объектов одинаковы. Это происходит, потому что сравниваются ссылки на объекты:

```js
console.log(tomato === strawberry);
// false

console.log(tomato === tomato)
// true
```