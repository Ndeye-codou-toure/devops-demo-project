# Stage 1 : Build avec Maven
FROM maven:3.8-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests && ls -la target/

# Stage 2 : Image finale
FROM eclipse-temurin:17-jdk
COPY --from=build /app/target/*.jar /opt/app/app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/opt/app/app.jar"]
