FROM node:alpine
WORKDIR "/app"
COPY ./package.json ./
RUN npm install
RUN curl -fsSL https://deb.nodesource.com/setup_${NODE_VERSION}.x | bash - \
  && apt-get update \
  && apt-get autoremove \
  && apt-get install -y nodejs
COPY . .
CMD ["npm","run","start"]
