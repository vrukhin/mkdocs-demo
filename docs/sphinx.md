# Sphinx

## Создание проекта

1. Создайте новый проект, следуя подсказкам мастера

    ```bash
    sphinx-quickstart
    ```

1. Отредактируйте `conf.py` по [инструкции](https://www.sphinx-doc.org/en/master/usage/configuration.html)

1. Запустите сервер

    ```bash
    sphinx-reload .
    ```

## Добавление страниц

В папке `sources` создайте страницы вашей документации в формате `.rst`. В каждой папке должен находиться файл `index.rst`, содержащий ссылки на остальные файлы.

## Сборка статического сайта

Для сборки статического сайта выполните команду

```bash
sphinx-build -M html sourcedir outputdir
```

При наличии make-файла сборку можно запустить командой

```bash
make html
```

## Добавление переводов

1. Добавьте в `conf.py` следующие строки

    ```python
    locale_dirs = ['locale/']
    gettext_compact = False
    ```

1. Запустите сборку в формат `gettext`

    ```bash
    make gettext
    ```

1. Сгенерируйте файлы локализации

    ```bash
    sphinx-intl update -p _build/gettext -l en
    ```

1. Добавьте переводы строк в файлы локализации

1. Выполните сборку

    ```bash
    make -e SPHINXOPTS="-D language='en'" html
    ```