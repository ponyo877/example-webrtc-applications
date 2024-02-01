FROM golang:1.21-alpine AS build
WORKDIR /src
RUN apk update
ADD . /src
RUN go mod download
RUN go build -o /websocket-server

FROM alpine:latest
WORKDIR /
COPY --from=build /websocket-server /websocket-server
ENTRYPOINT ["/websocket-server"]