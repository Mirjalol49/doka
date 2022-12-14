---
title: "`<caption>`"
description: "Добавляет подпись таблице."
authors:
  - solarrust
related:
  - css/flexbox-guide
  - html/figure-figcaption
  - css/grid-guide
tags:
  - doka
---

## Кратко

Тег `<caption>` нужен, чтобы добавить таблице подпись. В подписи лучше всего написать обобщающую информацию.

## Пример

```html
<table>
  <caption>Сводная таблица лайков</caption>
  ...
</table>
```

## Как пишется

Тег `<caption>` должен идти сразу после открывающего тега `<table>`. По умолчанию подпись визуально располагается сразу перед таблицей. Но её положением можно управлять при помощи свойства `caption-side`. Вне зависимости от визуального расположения подписи [скринридер](/a11y/screenreaders/) прочитает её перед таблицей.

Внутри тега можно располагать любые другие теги, нужные для группировки и оформления подписи.

## Как понять

Наличие подписи таблицы особенно важно для людей, использующих скринридеры. Вместо того чтобы слушать табличные данные, которые могут быть бесполезными удобнее прослушать подпись к таблице и решить, важна ли она.

## Подсказки

💡 Применимы любые CSS-свойства.
