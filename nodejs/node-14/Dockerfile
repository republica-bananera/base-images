# Usamos una imagen base con Node.js 14
FROM node:14 AS build

# Establecemos el directorio de trabajo
WORKDIR /app

# Copiamos el archivo package.json y package-lock.json (si existe)
COPY package*.json ./

# Instalamos las dependencias de la aplicación
RUN npm install

# Copiamos todo el código fuente de la aplicación
COPY . .

# Construimos el proyecto (si se requiere)
RUN npm run build  # Usar esto si tienes un script de build en tu package.json

# Usamos una imagen base más ligera para la ejecución (también con Node.js 14)
FROM node:14-slim

# Establecemos el directorio de trabajo para la ejecución
WORKDIR /app

# Copiamos las dependencias y los archivos construidos desde la etapa de build
COPY --from=build /app /app

# Exponemos el puerto que usará la aplicación (ajusta según sea necesario)
EXPOSE 3000  # O el puerto que tu aplicación utilice

# Ejecutamos la aplicación
CMD ["npm", "start"]
