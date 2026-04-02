# Base image
#FROM eclipse-temurin:17-jdk

# setting artifact path
#ARG artifact=target/spring-boot-web.jar

# copying artifact to /opt/app
#COPY ${artifact} /opt/app/spring-boot-web.jar

# exposing port
#EXPOSE 8080

# starting the application
#ENTRYPOINT ["java", "-jar", "/opt/app/spring-boot-web.jar"]

# Stage 1 : Build avec Maven
FROM maven:3.8-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2 : Image finale
FROM eclipse-temurin:17-jdk
COPY --from=build /app/target/spring-boot-web.jar /opt/app/spring-boot-web.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/opt/app/spring-boot-web.jar"]
