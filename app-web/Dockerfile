FROM node:10

ARG NODE_MAJOR_VERSION=10
ARG NODE_VERSION=10.15.3
ARG APP_VERSION=2.3.0

ENV INSTALL_PATH /home/app
ENV SUMMARY="Devhub App Web ${APP_VERSION}"  \
  DESCRIPTION="Devhub App Web ${APP_VERSION} running node nodejs ${NODE_VERSION} on Alpine Linux"
ENV LC_ALL=en_US.UTF-8 \
  LANG=en_US.UTF-8 

LABEL summary="$SUMMARY" \
  description="$DESCRIPTION"

RUN apt-get update && \
  yes | apt-get upgrade

RUN useradd --user-group --create-home --shell /bin/false app

USER app
WORKDIR $INSTALL_PATH

COPY . .
USER root
RUN chown -R app:app $INSTALL_PATH

RUN npm ci --silent

EXPOSE 8000

CMD [ "npm", "run", "dev" ]