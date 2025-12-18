#stage 1-building
FROM maven:3.5-eclipse-temurin-17 AS build

WORKDIR /app

COPY pom.xml ./

RUN mvn dependency:go-offline -B

COPY . .

RUN mvn clean package -DskipTests

#stage 2-serving
FROM eclipse-temurin:17-jre-alphine

WORKDIR /app

COPY --from=build /target/*.jar app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
