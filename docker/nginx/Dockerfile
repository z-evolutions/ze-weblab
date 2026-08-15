FROM node:22-trixie AS frontend

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm ci

COPY resources ./resources
COPY public ./public
COPY vite.config.js ./

RUN npm run build


FROM nginx:1.29-alpine

COPY public /var/www/html/public

COPY --from=frontend /app/public/build /var/www/html/public/build

COPY docker/nginx/default.conf /etc/nginx/conf.d/default.conf