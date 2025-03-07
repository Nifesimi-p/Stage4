# Use official Go image as the build stage
FROM golang:1.21 AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy Go module files first for dependency caching
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

# Copy the entire application source code
COPY . .

# Build the Go application
RUN go build -o auth-api

# Use a lightweight image for the final container
FROM alpine:latest

# Set work directory inside the container
WORKDIR /root/

# Copy the compiled binary from the builder stage
COPY --from=builder /app/auth-api .

# Expose the application port (change if necessary)
EXPOSE 8080

# Run the application
CMD ["./auth-api"]
