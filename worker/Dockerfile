FROM maven:3.5-jdk-8-alpine as build
# Choose a workdir
WORKDIR /usr/src/app
# Copy sources
COPY . .
# Build app (bin will be in /usr/src/app/target/release/rust-lang-docker-multistage-build)
RUN mvn dependency:resolve
RUN mvn package
ENV POSTGRES=db
ENV REDIS=redis

FROM openjdk:8-jre-alpine
# Copy bin from builder to this new image
COPY --from=build /usr/src/app/target/worker-jar-with-dependencies.jar /bin/
# Default command, run app
ENTRYPOINT ["java","-jar","/bin/worker-jar-with-dependencies.jar"]

#FROM maven:3.5-jdk-8-alpine
#
#RUN mkdir /app/
#ADD . /app/
#WORKDIR /app/
#
#RUN mvn dependency:resolve
#RUN mvn package
#
#FROM openjdk:8-jre-alpine
#COPY /app/target/worker-jar-with-dependencies.jar /app/worker-jar-with-dependencies.jar
#CMD [ "java -jar /app/worker-jar-with-dependencies.jar" ]
#ENTRYPOINT ["java","-jar","/app/target/worker-jar-with-dependencies.jar"]