🛠 Используйте [`await Promise.all([...])`](/js/promise-all/) для параллельного выполнения нескольких независимых асинхронных функций.

Используя `async/await`, мы делаем наш код последовательным: ожидаем выполнения одной асинхронной функции и лишь после запускаем другую. В примере ниже новости будут запрошены только после получения пользователя:

```js
async function getUser(){
  // Возвращает информацию о пользователе
}

async function getNews(){
  // Возвращает список новостей
}

const user = await getUser()
const news = await getNews()
```

Но, запустив `getNews` параллельно c `getUser`, мы в большинстве случаев получим результат быстрее. `Promise.all()` позволяет запустить запросы параллельно, при этом дожидаться результата мы можем как и раньше при помощи `await`:

```js
const [user, news] = await Promise.all([
  getUser(),
  getNews()
])
```

🛠 Не смешивайте синтаксис `async/await` и `Promise.then`, старайтесь применять один подход на проекте: так код легче читать и поддерживать.
