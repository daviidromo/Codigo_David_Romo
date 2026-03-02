# Etapa 1: Compilación
# Cambiamos a Node 20 para cumplir con los requisitos de Vite 7
FROM node:20-alpine AS build-stage
WORKDIR /app

# Copiamos archivos de dependencias
COPY package*.json ./

# Instalamos dependencias
RUN npm install

# Copiamos el resto del código
COPY . .

# Ejecutamos la compilación
RUN npm run build

# Etapa 2: Producción
FROM nginx:stable-alpine AS production-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]