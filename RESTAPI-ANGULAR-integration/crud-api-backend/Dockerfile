#stage 1

FROM maven:8-eclipse-temurin-17 AS build

WORKDIR /app

COPY pom.xml ./

RUN mvn dependency:go-offile -B

COPY . .

RUN mvn clean package -DskipTests

#stage 2
FROM eclipse-temurin:17-jre-alpine

COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
