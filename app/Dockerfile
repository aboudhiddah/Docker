FROM python:3.11-alpine

# Установка зависимостей
RUN apk add --no-cache gcc musl-dev postgresql-dev

# Создание непривилегированного пользователя
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Установка приложения
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Переход на непривилегированного пользователя
USER appuser

# Запуск приложения
CMD ["python", "main.py"]
