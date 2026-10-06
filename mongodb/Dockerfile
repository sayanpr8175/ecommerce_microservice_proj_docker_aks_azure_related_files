# Base image for the builder stage

FROM alpine:latest AS builder
WORKDIR /app
COPY mongodb-init ./
RUN apk add --no-cache openssl


# base image for MongoDB
FROM mongo:latest


# Copy initialization scripts from the builder stage to the MongoDB image
COPY --from=builder /app /docker-entrypoint-initdb.d


# Set the MongoDB environment variables
ENV MONGO_INITDB_DATABASE=OrdersDatabase

# Expose the MongoDB port
EXPOSE 27017