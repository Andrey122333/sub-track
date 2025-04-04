FROM node:18 AS base

WORKDIR /app
COPY package*.json ./
RUN npm install
EXPOSE 4000

# Этап разработки
FROM base AS dev
RUN npm install
COPY . .
CMD ["npm", "run", "dev"]

# Этап тестирования
FROM base AS test
RUN npm install
COPY . .
CMD ["npm", "test"]

# Продакшен-этап
FROM base AS prod
RUN npm install --production
COPY . .
RUN npm run build
CMD ["node", "dist/main.js"]