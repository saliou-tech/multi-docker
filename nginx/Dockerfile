FROM nginx
RUN curl -fsSL https://deb.nodesource.com/setup_${NODE_VERSION}.x | bash - \
  && apt-get update \
  && apt-get autoremove \
  && apt-get install -y nodejs
COPY ./default.conf /etc/nginx/conf.d/default.conf
