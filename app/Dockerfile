#https://docs.docker.com/build/building/multi-stage/

FROM golang:1.16 AS builder
WORKDIR /
RUN go get -d -v golang.org/x/net/html  
RUN go mod init fullcycle/desafio_docker_go
COPY main.go ./
RUN CGO_ENABLED=0 go build -a -installsuffix cgo -o app .

FROM scratch
COPY --from=builder /app ./
CMD ["./app"]  