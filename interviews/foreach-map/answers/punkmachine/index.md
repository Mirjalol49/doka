Методы `forEach()` и `map()` определены на нескольких структурах данных. Мы рассмотрим чем отличаются эти методы для массивов.

Оба метода принимают колбэк, который вызывается для каждого элемента. Разница в том, что метод `forEach()` ничего не возвращает, а метод `map()` возвращает новый массив с результатами вызова колбэка на каждом исходном элементе. Если переданный колбэк ничего не возвращает в новом массиве появится [`undefined`](/js/undefined/)

Вы можете вернуть значение и из колбэка для `forEach()` но оно никак не будет использоваться дальше.
```js
[1,2,3].forEach(a => a + 3);
```

Используя `map()` вы можете создавать цепочки вызовов. Если же вы будете использовать `forEach()` так сделать не получится.

```js
const myArray = [4, 2, 8, 7, 3, 1, 0];
const myArray2 = myArray.map(item => item * 2).sort((a, b) => a - b);

console.log(myArray); // [4, 2, 8, 7, 3, 1, 0]
console.log(myArray2); // [0, 2, 4, 6, 8, 14, 16]
```

В примере выше изменился только `myArray2`.

Для закрепления, реализуем ту же самую логику при помощи `forEach()`.

```js
const myArray = [4, 2, 8, 7, 3, 1, 0];
let myArray2 = [];

myArray.forEach(item => {
  myArray2.push(item * 2);
});

myArray2 = myArray2.sort((a, b) => a - b);

console.log(myArray); // [4, 2, 8, 7, 3, 1, 0]
console.log(myArray2); // [0, 2, 4, 6, 8, 14, 16]
```
