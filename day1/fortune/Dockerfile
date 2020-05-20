FROM node:latest

ENV APP_ROOT=/app APP_PORT=3000

# create APP_ROOT and cd in
WORKDIR ${APP_ROOT}

# copy the files and directory into image
ADD package.json .
ADD package-lock.json .
# install the dependencies
RUN npm ci

ADD main.js .
ADD public public
ADD views views

# healthcheck
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1

# tell what port we are using
EXPOSE ${APP_PORT}

ENTRYPOINT [ "node", "main.js" ]

# CMD [ "${APP_PORT}" ]
