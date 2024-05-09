# Base image
FROM alpine:3.7

# Update system and install dependencies (make gcc g++ and python are the equivalent for the build-essential package in the previous Dockerfile)
RUN apk update && \
    apk add nodejs

# Create and define work directory
WORKDIR /code

# Copy required files
COPY ./ /code

# Install required npm packages
RUN npm set progress=false && \
    npm install --silent

# Build application
RUN npm run build

# Create dedicated user to not run the application as root (security best practice)
RUN adduser -D -h /code -u 5000 nulldoot2k && \
    chown -R nulldoot2k:nulldoot2k /code

USER nulldoot2k

# Expose application port
EXPOSE 8080

# Define entrypoint
ENTRYPOINT ["npm", "run"]

# Define default command
CMD ["start"]
