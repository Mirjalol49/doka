---
title: "Что такое CI/CD"
description: "Технологии для автоматизации доставки приложений."
authors:
  - igsekor
editors:
  - tachisis
keywords:
  - deploy
  - интеграция
  - публикация
  - jenkins
  - github actions
  - gitlab ci
  - bitbucket pipelines
  - travis
  - puppeteer
  - selenium
related:
  - tools/bundlers
  - tools/docker
  - tools/version-control
tags:
  - article
---

## Кратко

Аббревиатура CI/CD означает «Continuous Integration/Continuous Delivery» — то есть «непрерывная интеграция/непрерывная доставка». Это подход к разработке, при котором задачи сборки, публикации, тестирования продукта полностью или частично автоматизированы. Очень часто автоматизация интегрирована в бизнес-процессы продуктовой команды или компании, но практики CI/CD прекрасно могут быть внедрены и в проекты, в которых участвует только один разработчик.

## Как понять

Технологии CI/CD стали активно проникать в процессы разработки программных продуктов, когда стало очевидно, что для большинства прикладных программ великолепно подходят практики Agile, о которых можно подробнее почитать в статье «[Методологии разработки и Agile](/tools/agile/)». Оказалось, что каждую итерацию цикла разработки можно ускорить с помощью автоматизации разных процессов. Типичную итерацию процесса разработки с применением CI/CD можно изобразить на схеме следующим образом:

![Схема применения CI/CD на итерации типичного проекта.](images/1.png)

Применение CI/CD стало очень хорошим решением, и вскоре появились первые инструменты. В мире веб-разработки это различные «[системы сборки](/tools/bundlers/)», «[менеджеры пакетов](/tools/package-managers/)» и инструменты для тестирования.

## Основные принципы

Поскольку речь идёт об интеграции и доставке приложений до потребителей, набор инструментов тесно связан с системой контроля версий, серверной инфраструктурой и средствами командного взаимодействия.

В основе разработки и использования CI/CD лежат следующие принципы:

- разделение ответственности заинтересованных сторон;
- снижение рисков;
- короткий цикл обратной связи;
- реализация среды.

В рамках гибкой методологии разработку приложения обеспечивают владельцы продукта, маркетологи, дизайнеры, разработчики, тестировщики, инженеры по инфраструктуре, пользователи продукта. Разделение ответственности означает, что ответственность за разные стороны продукта лежит на разных ролях. Интегрировать (автоматизировать) все процессы взаимодействия между ними как раз и помогают инструменты CI/CD.

Например, по запросу от пользователей или владельца продукта дизайнеры дорабатывают интерфейс, разработчики пишут код, исправляют ошибки и внедряют новую функциональность. Затем в дело вступают тестировщики, которым приложение приходит в собранном виде, пройдя все необходимые автоматические проверки на качество и правильность работы кода. После успешного тестирования пользователи получают готовый к использованию продукт, отмечают баги и видят, как функциональность может быть ещё расширена. Процесс циклически повторяется вновь и вновь.

Применение автоматизации процессов разработки снижает риск ошибок, позволяет оперативно чинить то, что не работает. Настройка инструментов CI/CD затрагивает и такую часть разработки, как создание единого окружения, в котором ведётся разработка программного продукта. Для разработчика это крайне важно.

Например, использование одних и тех же npm-пакетов, их версий и инструментов тестирования позволяет разрабатывать приложение по единым стандартам качества. Случайные ошибки из-за неправильного окружения или другой операционной системы практически исключены.

## Этапы интеграции и доставки приложений

Работа системы инструментов CI/CD основана на цикличности, что прекрасно укладывается в рамки гибкой методологии разработки программного обеспечения. Цикл применения инструментов состоит из следующих этапов:

- написание кода;
- сборка;
- ручное тестирование;
- релиз;
- развёртывание;
- поддержка и мониторинг;
- планирование.

### Написание кода

На этом этапе самым главным инструментом является система контроля версий. Обычно это [Git](https://git-scm.com). Важный элемент здесь — модель ветвления, то есть принципы использования веток в разработке. Например, в проектах на GitHub, как правило, используется модель ветвления [GitHub Flow](https://guides.github.com/introduction/flow/):

1. Разработчик делает форк репозитория к себе в аккаунт на GitHub или клонирует репозиторий на компьютер. Форк — это полная копия (зеркало) репозитория на какой-то определённый момент времени, которую можно обновлять при необходимости.
2. После этого разработчик вносит изменения в форке или в локальной копии. Хорошей практикой является создание новой ветки и работы в ней.
3. Затем формируется пул-реквест — это запрос на слияние с основной веткой.
4. В рамках пул-реквеста можно проверить все предложенные изменения, обсудить решения и прийти к консенсусу.
5. После утверждения всех изменений они вливаются в основную ветку репозитория.

Существуют и другие модели ветвления, например, Git-flow, о которой хорошо рассказывается в статье «[A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)» на английском языке и в переводе на русском «[Удачная модель ветвления для Git](https://habr.com/ru/post/106912/)».

### Сборка

После написания и первичного тестирования на локальном компьютере разработчика код попадает на сервер, и производится сборка. Тестовая или готовая к публикации сборка настраивается и работает на сервере. В последнее время для сборки чаще всего используются контейнеры, например, Docker-контейнеры. Подробнее о них можно почитать в серии статей о Docker:

- [Что такое Docker](/tools/docker/);
- [Как устроен Dockerfile](/tools/dockerfile/);
- [Управление данными в Docker](/tools/docker-data-management/);
- [Мультиконтейнерное приложение и Docker Compose](/tools/docker-compose/).

Для автоматизации сборки могут использоваться различные системы. Наиболее популярные из них:
- [Jenkins](https://www.jenkins.io);
- [GitHub Actions](/tools/github-actions/);
- [GitLab CI/CD](https://docs.gitlab.com/ee/ci/);
- [Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines);
- [JetBrains TeamCity](https://www.jetbrains.com/teamcity/).

Сборку поддерживают популярные и специализированные хостинги, например, [Netlify](https://www.netlify.com/products/build/).

### Тестирование

После первичной подготовки кода продукту назначается версия будущего релиза с пометкой номера тестовой сборки для детального автоматизированного и ручного тестирования. Например, если номер будущего релиза _v.2.4.5_, то номер первой тестовой сборки может быть указан так: _v.2.4.5-1_. На этом этапе преобладает ручное тестирование продукта, поиск и планирование исправления ошибок. После нескольких итераций продукт признаётся готовым к релизу и переходит на следующий этап тестирования.

На этом этапе широко применяются [интеграционные тесты](/js/integration-and-system-testing/), E2E-тесты, ручное и автоматизированное тестирование UI/UX. Для этого могут использоваться различные инструменты. Например, [Jest](https://jestjs.io) может покрыть задачи модульного, интеграционного и E2E-тестирования веб-приложения. Для генерации скриншотов веб-приложения и автоматического сравнения с эталоном можно использовать [Selenium](https://www.selenium.dev) или [Puppeteer](https://pptr.dev). При этом можно смоделировать не только загрузку веб-приложения и сохранить скриншоты экранов разных размеров, но и с помощью сценариев посмотреть, как будущий пользователь будет взаимодействовать с приложением.

### Релиз

Есть разные типы цикла релизов, о которых подробно рассказывается в статье «[Методологии разработки и Agile](/tools/agile/)». В зависимости от особенностей продукта, состава команды и задач владельцев продукта назначается периодичность релизов. Важен не только сам релиз, но и то, как работала команда на очередном витке.

Инструменты CI/CD на этом этапе отвечают в основном за сбор различной статистической информации. Это могут быть как пользовательские метрики (например, Яндекс.Метрика или Google Analytics), так и метрики, принятые внутри команды для отслеживания эффективности того или иного члена команды (например, можно отслеживать количество выполненных задач, скорость их выполнения, инициативность и профессиональный рост с помощью встроенных инструментов [Jira](https://www.atlassian.com/ru/software/jira), [Wrike](https://www.wrike.com) или [Trello](https://trello.com/home)).

### Развёртывание

Наступает этап доставки продукта до конечных потребителей. Сложность развёртывания продукта связана со сложностью инфраструктуры (с архитектурой построения серверов, различными оптимизациями загрузки и работы приложения, кэшированием). Простые веб-приложения особенного внимания с точки зрения инфраструктуры не требуют. Но есть крупные онлайн-магазины, поисковые системы, стриминговые сервисы, для которых инфраструктурные задачи могут быть чуть ли не самыми важными с точки зрения конкуренции на рынке.

### Поддержка и мониторинг

Наконец-то приложение доступно для рядовых пользователей. Здесь важны скорость и точность ответов на вопросы пользователей (то есть организация службы поддержки пользователей) и встроенная грамотная маркетинговая политика. Для решения этих задач существует множество инструментов, но мы не будем подробно на них останавливаться, поскольку это не относится к разработке. В основном эти инструменты не сильно отличаются от инструментов для обычной офисной работы в рамках крупной компании (IP-телефония, чаты, электронная почта, различные менеджеры задач, подготовка автоматических отчётов и другие программные и аппаратные инструменты). В поддержке современных продуктов часто используются голосовые помощники и чат-боты. Практически все эти инструменты не являются инструментами CI/CD, но почти всегда предоставляют API, чтобы можно было настроить глубокую интеграцию между различными этапами для повышения качества продукта.

### Планирование

Важным этапом является и планирование следующего цикла. На основе пользовательского опыта формируется бэклог задач для реализации, назначаются приоритеты и исполнители. После этого цикл CI/CD замыкается.

<aside>

👆 Необходимо помнить, что некоторые этапы CI/CD могут быть скорректированы или пропущены вовсе. Конкретная детализация зависит от конкретного продукта, состава и квалификации команды, а также особенностей выведения продукта на рынок.

</aside>

## Преимущества и недостатки

Преимущества:

- Инструменты CI/CD позволяют быстро выводить программный продукт на рынок, исправлять ошибки, внедрять новую функциональность.
- Автоматизация позволяет снизить нагрузку на членов команды, облегчает тестирование и уменьшает количество ошибок в каждой итерации. Главный плюс — это быстрая обратная связь.
- Гибкий план позволяет быстро перераспределять ресурсы команды на решение действительно важных задач.

Недостатки:

- Часто инструменты CI/CD воспринимаются как швейцарский нож, который может справиться с любыми задачами. При недостатке опыта это может приводить к существенному усложнению процессов в команде.
- Инструменты CI/CD не могут решить проблемы взаимодействия внутри команды, обо всём придётся договариваться.
- Все члены команды должны работать в единой экосистеме.