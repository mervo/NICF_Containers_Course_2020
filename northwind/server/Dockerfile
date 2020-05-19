FROM node:latest

ENV APP_ROOT=/app APP_PORT=3000
ENV DB_USER=root DB_PASSWORD=changeit

WORKDIR ${APP_ROOT}

ADD package.json .
ADD package-lock.json .
RUN npm ci

ADD main.js .
ADD config config 
ADD public public
ADD views views

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1

EXPOSE ${APP_PORT}

ENTRYPOINT [ "node", "main.js" ]
