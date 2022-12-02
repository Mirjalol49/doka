---
title: "CSS-правило"
description: "То, из чего состоят таблицы стилей."
authors:
  - solarrust
keywords:
  - правило стилей
related:
  - css/class-selector
  - css/combined-selectors
  - html/class
tags:
  - doka
---

## Кратко

Весь CSS состоит из однотипных блоков — CSS-правил. Каждое правило состоит из как минимум одного селектора и одной пары свойство-значение.

## Пример

Написанное ниже правило _найдёт_ все заголовки второго уровня в HTML и покрасит их в зелёный цвет:

```css
h2 {
  color: #32a846;
}
```

## Как пишется

CSS-правило состоит из нескольких обязательных элементов:

- селектор;
- свойство;
- значение.

### Селектор

При помощи селектора мы _говорим_ браузеру, к какому именно элементу будут применяться свойства.

Есть разные типы селекторов. Подробнее о них можно почитать в отдельных статьях:

- [универсальный селектор](/css/universal-selector/);
- [селекторы по тегу](/css/tag-selector/);
- [селектор по классу](/css/class-selector/);
- [селектор по идентификатору](/css/id-selector/);
- [селектор по атрибуту](/css/attribute-selector/).

Можно написать правило сразу для нескольких селекторов, перечислив их через запятую:

```css
.first-selector,
.next-selector {
  color: #6e4aff;
}
```

Селекторы можно разным образом комбинировать между собой. Подробнее в статье про [комбинированные селекторы](/css/combined-selectors/).

Сразу после селектора пишутся фигурные скобки `{ }`. Внутри них будут перечислены свойства и значения.

### Пара свойство-значение

Свойства и их значения рассмотрим в паре, потому что они не существуют друг без друга.

Свойство указывает какой именно визуальный аспект выбранного тега будет изменяться.

А вот на то, как именно он будет изменяться, указывает значение этого свойства.

В конце строки обязательно нужно поставить точку с запятой. Иначе браузер _склеит_ свойства и они не будут работать.

## Как понять

К селектору применятся свойства, сгруппированные в фигурных скобках. Один и тот же селектор может повторяться не один раз. За то, какие свойства в итоге применятся к элементу, отвечает каскад.

## Подсказки

💡 Очень частая ошибка — забытая точка с запятой. Обращайте на это внимание!