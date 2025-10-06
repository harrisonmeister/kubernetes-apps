FROM golang:1.22.4-alpine3.20 AS build-env

WORKDIR /tmp/web-app

COPY . .

RUN apk update && apk upgrade --no-cache && \
	CGO_ENABLED=0 GOOS=linux go build 

FROM scratch
COPY --from=build-env /tmp/web-app/terranova-web-app /app/terranova-web

EXPOSE 8080
CMD ["/app/terranova-web"]