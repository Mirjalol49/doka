---
title: "`.forEach()`"
description: "Сколькими способами можно обойти массив? Это ещё один способ, но без явного описания цикла."
authors:
  - windrushfarer
contributors:
  - nlopin
  - skorobaeus
editors:
  - tachisis
related:
  - js/loop
  - js/function-as-datatype
  - js/programming-paradigms
tags:
  - doka
---

## Кратко

Метод массива `forEach()` позволяет применить колбэк-функцию ко всем элементам массива. Можно использовать вместо классического цикла [`for`](/js/for/). В отличие от него `forEach()` выглядит более читабельным и понятным.

## Пример

```js
const numbers = [1, 2, 3, 4]

numbers.forEach((num) => {
  const square = num * num
  console.log('Квадрат числа равен: ' + square)
})
```

Выведет:

```
Квадрат числа равен: 1
Квадрат числа равен: 4
Квадрат числа равен: 9
Квадрат числа равен: 16
```

Интерактивный пример:

<iframe title="Работа Array.forEach — Array.forEach — Дока" src="demos/index/" height="610"></iframe>

Совсем любопытные могут заглянуть в исходники, чтобы посмотреть как `forEach()` активно используется в коде этого примера.

## Как пишется

Для того чтобы использовать `forEach()`, понадобится колбэк-функция, которую необходимо передавать в метод. Функцию можно объявить заранее:

```js
function sliceFruit(fruit) {
  console.log('Разрезаю ' + fruit + '!')
}

const fruits = ['🍎', '🍊', '🍋', '🍓', '🥝']

fruits.forEach(sliceFruit)
```

Или создать её прямо в месте вызова:

```js
const food = ['🍔', '🍟', '🍦']

food.forEach((item) => {
  console.log('Мам, купи ' + item + '!')
})
```

Важно знать, какие параметры принимает колбэк. Всего их три:

- `item` — элемент массива в текущей итерации;
- `index` — индекс текущего элемента;
- `arr` — сам массив, который мы перебираем.

Вернёмся к примеру с едой:

```js
const food = ['🍔', '🍟', '🍦']

food.forEach((item, index, arr) => {
  console.log('Текущий элемент ' + item)
  console.log('Его индекс ' + index)
  console.log('Исходный массив ' + arr)
})
```

Выведет:

```
Текущий элемент 🍔
Его индекс 0
Исходный массив ['🍔', '🍟', '🍦']
Текущий элемент 🍟
Его индекс 1
Исходный массив ['🍔', '🍟', '🍦']
Текущий элемент 🍦
Его индекс 2
Исходный массив ['🍔', '🍟', '🍦']
```

## Как понять

Метод `forEach()` можно использовать, когда вам необходимо совершить одну и ту же операцию над всеми элементами массива.

Хотя в JavaScript уже есть возможность делать это, используя цикл `for`, метод `forEach()` — это отличная альтернатива с рядом преимуществ:

- Использование метода `forEach()` является _декларативным_ способом обозначить нашу операцию. С точки зрения читабельности кода это больше приближено к естественному языку и лаконично.
- Позволяет удобно получать элемент в текущей итерации, без необходимости всякий раз обращаться к массиву по индексу.

Однако вместе с тем мы получаем и несколько недостатков:

- В `forEach()` не будут работать [`return`](/js/return/), `break` и `continue`, а следовательно, мы никак не можем прервать или пропустить итерацию. Потому, если для решения задачи необходимо воспользоваться каким-либо из этих операторов, придётся использовать обычный цикл `for`.
- `forEach()` обрабатывает элементы массива в прямом порядке, то есть мы не можем пройти по массиву с конца.

💡 Метод `forEach()` автоматически встроен в любой массив.

Сработает:

```js
const empty = []
const someNums = [1, 2, 3]

console.log(empty.forEach)
// Выведет функцию
console.log(someNums.forEach)
// И здесь тоже

const obj = {}
console.log(obj.forEach)
// undefined, потому что у объектов нет такого метода
```