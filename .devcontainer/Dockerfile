FROM python:3.11-slim

# Установка системных зависимостей
RUN apt-get update && apt-get install -y \
    curl git openssh-client \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Установка Rust
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y --profile minimal
ENV PATH="/root/.cargo/bin:${PATH}"

# Создаем рабочую директорию
WORKDIR /workspace

# Копируем requirements.txt в контейнер
COPY requirements.txt /tmp/pip-tmp/

# Устанавливаем зависимости
RUN pip install --no-cache-dir -r /tmp/pip-tmp/requirements.txt

# Очистка
RUN rustup self uninstall -y && \
    rm -rf /root/.cargo/registry