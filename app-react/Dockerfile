# build do código
FROM node:16 as builder

WORKDIR /app

COPY . .

RUN npm ci --silent

RUN npm run build

# configruando nginx
FROM nginx:1.21.3-alpine

COPY ./nginx.conf /etc/nginx/nginx.conf

COPY --from=builder /app/build /usr/share/nginx/html
