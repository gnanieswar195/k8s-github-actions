FROM golang:1.21 AS builder
WORKDIR /app
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o app .

FROM alpine:latest
WORKDIR /root/
COPY --from=builder /app/app .
RUN chmod +x /root/app  # Ensure it's executable

EXPOSE 8080
CMD ["./app"]

