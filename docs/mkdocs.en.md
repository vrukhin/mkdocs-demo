# MkDocs

## Project Creation

1. Create a new project

    ```bash
    mkdocs new .
    ```

1. Edit `mkdocs.yml` according to the
[instructions](https://squidfunk.github.io/mkdocs-material/creating-your-site/#minimal-configuration)

    **Example**

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
   
1. Start the server

    ```bash
    mkdocs serve
    ```

## Adding Pages

In the `docs` folder, create your documentation pages in `.md` format and add
them to `mkdocs.yml`. The documentation can have a multi-level structure.

**Example**

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

## Building a Static Site

To build a static site, run the command

```bash
mkdocs build
```

The generated files can be uploaded to a web server.

!!! tip

    For offline documentation distribution, build using the [appropriate plugin](https://squidfunk.github.io/mkdocs-material/setup/building-for-offline-usage/)

## Adding Translations

1. Add localization plugin settings to `mkdocs.yml`
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
1. Generate localization files
   ```bash
   md2po filname.md --quiet --save --po-filepath locale/en/LC_MESSAGES/filename.po
   ```
1. Add string translations to localization files
1. Generate markdown files
   ```bash
   po2md filename.md --pofiles locale/en/LC_MESSAGES/filename.po --quiet --save filename.en.md
   ```
1. Run the build
   ```bash
   mkdocs build
   ```
