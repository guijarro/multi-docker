FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
COPY ./public ./
COPY ./README.md ./
COPY ./src ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./ngnix/default.con /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /use/share/nginx/html

