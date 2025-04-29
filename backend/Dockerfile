FROM golang:1.24.2-alpine3.21

WORKDIR /app

COPY go.mod go.sum ./

RUN go mod tidy

EXPOSE 8080

CMD ["go", "run", "main.go"]