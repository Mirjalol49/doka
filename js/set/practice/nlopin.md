🛠 С помощью `Set` можно легко получить массив уникальных элементов из массива неуникальных с помощью конструктора и [спред-синтаксиса](/js/spread/):

```js
const nonUnique = [1, 2, 3, 4, 5, 4, 5, 1, 1]
const uniqueValuesArr = [...new Set(nonUnique)]

console.log(uniqueValuesArr)
// [1, 2, 3, 4, 5]
```

Это не самый оптимальный способ преобразования с точки зрения скорости работы, но самый удобный с точки зрения количества кода.
