# Usamos una imagen base con Maven y JDK 21 para la construcción
FROM maven:3.9.1-openjdk-21-slim AS build

# Establecemos el directorio de trabajo
WORKDIR /app

# Copiamos el archivo pom.xml
COPY pom.xml /app/

# Descargamos las dependencias de Maven
RUN mvn dependency:go-offline

# Copiamos el código fuente
COPY src /app/src/

# Ejecutamos el comando de Maven para instalar las dependencias y construir la aplicación
RUN mvn clean install -DskipTests

# Usamos una imagen ligera de OpenJDK 21 para ejecutar la aplicación
FROM openjdk:21-jdk-slim

# Establecemos el directorio de trabajo para la ejecución
WORKDIR /app

# Copiamos el código de la construcción desde la etapa anterior (incluso los archivos generados en target)
COPY --from=build /app/target /app/target

# Exponemos el puerto de la aplicación (ajusta según tu aplicación)
EXPOSE 8080

# Ejecutamos la aplicación con Maven (en lugar de ejecutar el .jar directamente)
CMD ["mvn", "spring-boot:run"]
