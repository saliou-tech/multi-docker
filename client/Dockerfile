FROM node:alpine as  builder
RUN apk add --update nodejs npm
WORKDIR '/app'

COPY ./package.json ./

RUN npm install


COPY . .

RUN npm run build

FROM nginx

RUN apk add --update nodejs npm


#RUN npm install
EXPOSE 3000

COPY ./nginx/default.conf  /etc/nginx/conf.d/default.conf

COPY --from=builder /app/build /usr/share/nginx/html
