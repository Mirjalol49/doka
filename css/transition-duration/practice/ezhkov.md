🛠 Лучше не экономить символы, и всегда делать количество времён равным количеству свойств. Но если все свойства должны меняться за одно и то же время, то можно и сэкономить 😈:

```css
.box {
  transition-property: opacity, visibility, transform;
  transition-duration: 0.3s;
}
```