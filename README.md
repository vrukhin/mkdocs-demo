# Запуск проекта

1. Установите [Docker](https://docs.docker.com/get-started/get-docker/) и [VS Code](https://code.visualstudio.com/)
1. Установите расширение [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) для VS Code
1. Клонируйте [репозиторий](https://github.com/vrukhin/MkDocs-demo.git)
1. VS Code автоматически предложит открыть проект в контейнере
1. Веб-сервер с собранным сайтом запустится автоматически и будет доступен по адресу http://localhost:8000

Чтобы вручную открыть проект в контейнере, вызовите `View` -> `Comand Palette` -> `Open Folder in Container`

После внесения изменений в `Dockerfile` или `devcontainer.json` вызовите `View` -> `Comand Palette` -> `Rebuild and Reopen in Container`