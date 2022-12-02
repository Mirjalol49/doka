---
title: "`font-style`"
authors:
  - doka-dog
contributors:
  - skorobaeus
keywords:
  - стиль шрифта
  - курсив
  - наклонное начертание
tags:
  - doka
---

## Кратко

Определяет начертание шрифта: обычное, <span style="font-style: italic">курсивное</span> или <span style="font-style: oblique">наклонное</span>.

## Пример

Попробуем выделить курсивом текст всего абзаца:

```html
<body>
  <h1>Текст ниже мы написали курсивом</h1>
  <p>
    Этот текст написан курсивом. А мог быть написан наклонным шрифтом, но вы всё
    равно бы это не отличили.
  </p>
</body>
```

```css
body {
  font-family: "Roboto", sans-serif;
}
p {
  font-style: italic;
}
```

<iframe title="Начертание шрифта" src="demos/font-style/" height="300"></iframe>

## Как понять

У большинства шрифтов есть несколько вариантов написания: стандартный, _курсивный_ или **жирный**. Чтобы задать курсивное написание, используй `font-style: italic`.

Ещё есть наклонный шрифт, который задаётся через `font-style: oblique`. Он очень похож на курсив, но по сути, это его имитация, которую используют, если у выбранного шрифта нет курсивного написания. Нужно помнить, что `oblique` может выглядеть хуже по качеству, чем курсивный шрифт. Это особенно заметно при печати страницы.

## Как пишется

Для `font-style` можно выбрать одно из четырёх значений:

- `normal` — обычное начертание текста (значение по умолчанию).
- `italic` — курсивное начертание.
- `oblique` — наклонное начертание, которое можно использовать, если у шрифта нет курсивного варианта начертания.

```css
.normal {
  font-style: normal;
}

.italic {
  font-style: italic;
}

.oblique {
  font-style: oblique;
}
```