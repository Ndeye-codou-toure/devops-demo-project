# Base image
FROM eclipse-temurin:17-jdk

# setting artifact path
ARG artifact=target/spring-boot-web.jar

# copying artifact to /opt/app
COPY ${artifact} /opt/app/spring-boot-web.jar

# exposing port
EXPOSE 8080

# starting the application
ENTRYPOINT ["java", "-jar", "/opt/app/spring-boot-web.jar"]
