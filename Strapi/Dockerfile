FROM node:10.10.0-jessie

MAINTAINER @Mikamakusa

ARG URL_PROXY
ARG LOGIN_PROXY
ARG PASS_PROXY
ARG STRAPI_SCRIPT
ARG STRAPI_VERSION

ENV http_proxy http://${LOGIN_PROXY}:${PASS_PROXY}@${URL_PROXY}
ENV https_proxy http://${URL_PROXY}
ENV HTTPS_PROXY http://${URL_PROXY}
ENV HTTP_PROXY http://${URL_PROXY}

RUN npm config set http-proxy $http_proxy && \
	npm config set https-proxy $http_proxy && \
	npm config set proxy $http_proxy && \
    echo Acquire::http::proxy \"http://${LOGIN_PROXY}:${PASS_PROXY}@${URL_PROXY}\"; > /etc/apt/apt.conf.d/Proxy && \
	echo Acquire::https::proxy \"http://${LOGIN_PROXY}:${PASS_PROXY}@${URL_PROXY}\"; >> /etc/apt/apt.conf.d/Proxy && \
    apt-get install -y git curl

WORKDIR /opt/
RUN git config --global http.proxy http://${LOGIN_PROXY}:${PASS_PROXY}@${URL_PROXY} && \
	git config --global https.proxy http.proxy http://${LOGIN_PROXY}:${PASS_PROXY}@${URL_PROXY} 

WORKDIR /opt/strapi
RUN npm install -g strapi@${STRAPI_VERSION} pm2

WORKDIR /usr/src/api
COPY ${STRAPI_SCRIPT} strapi.sh
COPY process.yml process.yml

EXPOSE 1337 4000

CMD ["./strapi.sh"]