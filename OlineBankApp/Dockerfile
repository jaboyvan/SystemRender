FROM maven:3.8.5-openjdk-17 AS build

WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline

COPY src ./src
RUN mvn clean package -DskipTests
FROM openjdk:8-jre-slim

WORKDIR /app
COPY --from=build /app/target/BankSystem-0.0.1-SNAPSHOT.jar /app/BankSystem.jar
EXPOSE 9090

CMD ["java", "-Xmx512m", "-jar", "BankSystem.jar"]