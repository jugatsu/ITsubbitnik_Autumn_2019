FROM golang:1.13-buster@sha256:d87b62b2d26b700a886d16b9405f2c38467be81b084f3908e111478762d76d82 as build

WORKDIR /app
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o app

FROM gcr.io/distroless/static-debian10:nonroot@sha256:5deee10d484f69514f63e7f36156b94d03afc4f46da3869078b7b3d64d941a62
COPY --from=build --chown=nonroot:nonroot /app /app
WORKDIR /app

ENV TZ=Europe/Moscow

CMD ["./app"]
