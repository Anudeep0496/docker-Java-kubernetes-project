FROM openjdk:17-jdk-slim
WORKDIR /app
ADD target/stockmanager-1.0.0.jar app.jar
EXPOSE 8030
ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "app.jar"]
