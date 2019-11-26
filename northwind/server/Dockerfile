FROM node:latest

# How an image is build
# Set environment variables
ENV APP_ROOT=/app APP_PORT=3000 DB_HOST=localhost DB_PORT=3306 DB_USER=root DB_PASSWORD=changeit INSTANCE_IP_ADDRESS=localhost

# Create directory and cd into it
WORKDIR ${APP_ROOT}

# Copy Files into the image
# files will be copied into /app
ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD config config
ADD public public
ADD views views

# Install dependencies
RUN npm install

# How an image is provisioned

# Expose Port
EXPOSE ${APP_PORT}/tcp

HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

ENTRYPOINT [ "node", "main.js" ]
CMD [ "" ]