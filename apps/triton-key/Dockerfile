FROM golang:1.22.4-alpine3.20 AS build-env

WORKDIR /tmp/app

COPY . .

RUN apk update && apk upgrade --no-cache && \
	CGO_ENABLED=0 GOOS=linux go build -o triton-key-app

FROM scratch
COPY --from=build-env /tmp/app/triton-key-app /app/triton-key

EXPOSE 8080
CMD ["/app/triton-key"]