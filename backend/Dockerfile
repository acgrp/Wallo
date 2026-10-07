FROM gradle:8.7-jdk17 AS build

WORKDIR /workspace
COPY . .
RUN chmod +x gradlew && ./gradlew --no-daemon clean war

FROM tomcat:9.0-jdk17-temurin
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build /workspace/build/libs/ROOT.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
