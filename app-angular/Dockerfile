# build do código
FROM node:16 as builder

WORKDIR /app

COPY . .

RUN npm ci --silent

# npm run build -- --deploy-url /angular/
RUN npm run build -- --base-href /angular/

# configruando nginx
FROM nginx:1.21.3-alpine

COPY ./nginx.conf /etc/nginx/nginx.conf

COPY --from=builder /app/dist/app-angular /usr/share/nginx/html
