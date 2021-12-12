FROM node:alpine as  builder

RUN apk add --update nodejs npm
WORKDIR '/app'

COPY ./package.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx
ARG NODE_VERSION=14
RUN curl -fsSL https://deb.nodesource.com/setup_${NODE_VERSION}.x | bash - \
  && apt-get update \
  && apt-get autoremove \
  && apt-get install -y nodejs


#RUN npm install
EXPOSE 3000

COPY ./nginx/default.conf  /etc/nginx/conf.d/default.conf

COPY --from=builder /app/build  /usr/share/nginx/html
