FROM openjdk:11-jdk-slim@sha256:fb54ed3516242995d86c53346463a3509f9baf74a9178c066bdbcc5c1bdafc66 AS build
COPY . /app/examples
WORKDIR /app
RUN javac examples/*.java
RUN jar cfe main.jar examples.HelloJava examples/*.class

FROM gcr.io/distroless/java:11@sha256:f9fe0de7f8ded68f757d99e9d165b96e89e00d4cef80d204aa76bc0b8ffc4576
COPY --from=build --chown=nonroot:nonroot /app /app
WORKDIR /app
USER nonroot
CMD ["main.jar"]
