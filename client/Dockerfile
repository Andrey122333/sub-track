# Этап сборки
FROM node:18 AS build

WORKDIR /app

ARG VITE_API_URL=http://app:4000
ENV VITE_API_URL=$VITE_API_URL

# Копируем package.json и устанавливаем зависимости
COPY package.json ./
RUN npm install --include=dev

# Копируем исходники
COPY . .

# Собираем приложение для продакшн
RUN npm run build

# Этап тестов
FROM node:18 AS test

WORKDIR /app

ARG VITE_API_URL=http://app:4000
ENV VITE_API_URL=$VITE_API_URL

# Копируем package.json и устанавливаем зависимости
COPY package.json ./
RUN npm install --include=dev

# Копируем исходники
COPY . .

# Выполняем тесты
CMD ["npm", "run", "test"]
