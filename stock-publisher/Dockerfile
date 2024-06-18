# Schritt 1: Build-Stage
FROM golang:1.22.3 AS builder

# Setzen Sie das Arbeitsverzeichnis
WORKDIR /app

# Kopieren Sie den Go-Modul-Definitionen und den Quellcode ins Arbeitsverzeichnis
COPY go.mod go.sum ./

# Install the dependencies
RUN go mod download

# Copy the source code to the container
COPY . .

RUN go build -o main .

# Setzen Sie die Umgebungsvariablen
ENV RABBITMQ_URL=amqp://stockmarket:supersecret123@localhost:5672/
ENV TICKER_INTERVAL=1

CMD ["./main"]