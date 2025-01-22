# /app /usr /lib
FROM node:22.12.0-alpine3.21

# cd /app
WORKDIR /app

# Destino /app
COPY package.json ./

# Instalar dependencias
RUN npm install

# Destino /app
COPY .  .

# Ejecutar testing
RUN npm run test

# Comando run app.js
CMD ["node", "app.js"]
