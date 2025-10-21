FROM golang:1.22.4-alpine3.20 AS build-env

WORKDIR /tmp/app

COPY . .

RUN apk update && apk upgrade --no-cache && \
	CGO_ENABLED=0 GOOS=linux go build -o seascape-core-app

FROM scratch
COPY --from=build-env /tmp/app/seascape-core-app /app/seascape-core

EXPOSE 8080
CMD ["/app/seascape-core"]