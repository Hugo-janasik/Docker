FROM maven:3.5-jdk-8-alpine as build
# Choose a workdir
WORKDIR /usr/src/app
# Copy sources
COPY . .
RUN mvn dependency:resolve
RUN mvn package

FROM openjdk:8-jre-alpine
ENV POSTGRES=db
ENV REDIS=redis
# Copy bin from builder to this new image
COPY --from=build /usr/src/app/target/worker-jar-with-dependencies.jar /bin/
# Default command, run app
ENTRYPOINT ["java","-jar","/bin/worker-jar-with-dependencies.jar"]
