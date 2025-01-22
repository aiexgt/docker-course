# /app /usr /lib
FROM node:22.12.0-alpine3.21

# cd /app
WORKDIR /app

# Destino /app
COPY package.json ./

# Installar dependencias
RUN npm install

# Destino /app
COPY app.js  ./

# Comando run app.js
CMD ["node", "app.js"]
