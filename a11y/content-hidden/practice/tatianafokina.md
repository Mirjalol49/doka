🛠 По идее, скрытый контент с помощью класса `.visually-hidden` не влияет на поисковую выдачу в Google и [не нарушает правила](https://developers.google.com/search/docs/essentials/spam-policies#hidden-text-and-links), если делаете это для улучшения доступности. Однако наверняка знать не может никто кроме самого Google.

🛠 Декоративные картинки из [`<img>`](/html/img/), у которых нет смысловой нагрузки, скрывайте от скринридеров пустым атрибутом `alt`. Не стоит усложнять код и добавлять `aria-hidden` или что-то ещё.
