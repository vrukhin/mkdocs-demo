# MkDocs

## Создание проекта

1. Создайте новый проект

    ```bash
    mkdocs new .
    ```

1. Отредактируйте `mkdocs.yml` по [инструкции](https://squidfunk.github.io/mkdocs-material/creating-your-site/#minimal-configuration)

    **Пример**

    ```yaml
    site_name: Название сайта
    site_url: https://myawesomewebsite.com

    plugins:
        - search

    theme:
    name: material
    language: ru

    features:
        - header.autohide
        - toc.follow

        - search.suggest
        - search.highlight
        - search.share

    nav:
        - Главная: index.md
        - MkDocs: mkdocs.md
        - Sphinx: sphinx.md
    ```

1. Запустите сервер

    ```bash
    mkdocs serve
    ```

## Добавление страниц

В папке ``docs`` создайте страницы вашей документации в формате ``.md`` и добавьте их в ``mkdocs.yml``. Документация может иметь многоуровневую структуру.

**Пример**

```yaml
nav:
  - Главная: index.md
  - Установка:
    - setup/index.md
    - Подготовка сервера: setup/prepare.md
    - Установка пакетов: setup/install.md
    - Подключение к серверу: setup/connect.md
  - Администрирование:
    - administration/index.md
    - Конфигурирование сервера: administration/config.md
    - Управление сессиями: administration/sessions.md
    - Журнал событий: administration/journal.md
```

## Сборка статического сайта

Для сборки статического сайта выполните команду

```bash
mkdocs build
```

Собранные файлы можно загрузить на веб-сервер.

!!! tip "Совет"

    Для распространения документации оффлайн выполняйте сборку с использованием [соответствующего плагина](https://squidfunk.github.io/mkdocs-material/setup/building-for-offline-usage/)

## Добавление переводов

1. Добавьте настройки плагина локализации в ``mkdocs.yml``

    ```yaml
    plugins:
      - i18n:
          default_language: ru
          languages:
            - locale: ru
              default: true
              name: Russian
              build: true
            - locale: en
              name: English
              build: true
              site_name: MkDocs Example
    ```

1. Сгенерируйте файлы локализации

    ```bash
    md2po filname.md --quiet --save --po-filepath locale/en/LC_MESSAGES/filename.po
    ```

1. Добавьте переводы строк в файлы локализации
1. Сгенерируйте файлы markdown

    ```bash
    po2md filename.md --pofiles locale/en/LC_MESSAGES/filename.po --quiet --save filename.en.md
    ```

1. Выполните сборку

    ```bash
    mkdocs build
    ```