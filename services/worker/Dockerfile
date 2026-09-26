# Stage One: Build Stage
FROM golang:1.23 AS build
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN go build -o server .

# Stage Two: Production Stage
FROM debian:bookworm-slim
WORKDIR /app
COPY --from=build /app/server .
CMD ["./server"]