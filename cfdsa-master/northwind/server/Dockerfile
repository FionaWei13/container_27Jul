  # this image will be baed on Node: v14
  FROM node:14

  # environment variable to define my workspace
  ENV APP_DIR=/app APP_PORT=3000 DB_USER=root DB_PASSWORD=changeit

  #Environment variable for DB

  # ENV DB_USER=root DB_PASSWORD=changeit

  # create and cd into APP_DIR
  # mkdir /app
  # cd /app

  WORKDIR ${APP_DIR}

  # copy the file from fortune into /application
  # Add local image

  ADD main.js .
  ADD package.json .
  ADD package-lock.json .

  # copy the directories
  ADD config config
  ADD public public
  ADD views views

  # install the dependencies - package.json
  RUN npm install

  ## Running the image
  # Add healthcheck
  HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1

  # the port the application is exposing
  EXPOSE ${APP_PORT}

  # run the Application
  ENTRYPOINT ["node","main.js"]
