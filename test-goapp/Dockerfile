FROM golang:1.21 AS build
WORKDIR /goapp
COPY go.mod ./
COPY go.sum ./
RUN go mod download && go mod verify
COPY main.go ./
RUN go build -o /test-goapp

FROM ubuntu:latest

COPY --from=build /test-goapp /test-goapp

ENTRYPOINT ["/test-goapp"]
