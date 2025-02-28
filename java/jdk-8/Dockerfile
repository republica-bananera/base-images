# Usamos una imagen base oficial de OpenJDK 8
FROM openjdk:8-jdk-alpine

# Establecemos el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copiamos los archivos de la aplicación al contenedor (ajusta la ruta según sea necesario)
COPY . /app

# Exponemos el puerto donde la aplicación escuchará (ajusta el puerto según tu aplicación)
EXPOSE 8080

# Comando por defecto para ejecutar la aplicación (ajusta según el archivo .jar)
CMD ["java", "-jar", "mi-aplicacion.jar"]
