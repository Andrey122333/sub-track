FROM node:18


ARG VITE_API_URL=http://app:4000
ENV VITE_API_URL=$VITE_API_URL

WORKDIR /app

# Установка зависимостей
COPY package.json ./
RUN npm install --include=dev

# Копирование исходников
COPY . .

# Для production-сборки можно добавить:
RUN npm run build