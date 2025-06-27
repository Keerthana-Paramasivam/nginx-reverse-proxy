# ---- Stage 1: Build ----
FROM golang:1.20-alpine AS builder

WORKDIR /app
    
COPY . .
    
RUN go build -o service1 main.go
    
# ---- Stage 2: Runtime ----
FROM alpine:3.18
    
WORKDIR /app
    
COPY --from=builder /app/service1 .
    
EXPOSE 8001
    
CMD ["./service1"]
    
