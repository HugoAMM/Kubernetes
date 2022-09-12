FROM openjdk:8-jdk-slim
COPY "./target/inventory-web-1.0-SNAPSHOT.jar" "app.jar"
EXPOSE 8090
ENTRYPOINT [ "java", "-jar", "app.jar" ]
