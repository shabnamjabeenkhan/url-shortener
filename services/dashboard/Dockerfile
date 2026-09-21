# Stage One: Build Stage
FROM golang:1.22 AS build
WORKDIR /app
COPY go.mod .
RUN go mod download
COPY . . 
RUN go build -o server .
EXPOSE 8081
CMD []


# Stage Two: Production Stage
FROM golang:1.22 
WORKDIR /app
