# BUILDX
# docker buildx build --platform linux/amd64,linux/arm64,linux/arm/v7 \
#    -t klerith/cron-ticker:latest --push .

# /app /usr /lib
# FROM --platform=linux/amd64 node:22.12.0-alpine3.21
# FROM --platform=$BUILDPLATFORM node:22.12.0-alpine3.21
FROM node:22.12.0-alpine3.21

# cd app
WORKDIR  /app

# Dest /app
COPY package.json ./

# Instalar las dependencias
RUN npm install

# Dest /app
COPY . .

# Realizar testing
RUN npm run test

# Eliminar archivos y directorios no necesarios en PROD
RUN rm -rf tests && rm -rf node_modules

# Unicamente las dependencias de prod
RUN npm install --prod


# Comando run de la imagen
CMD [ "node", "app.js" ]