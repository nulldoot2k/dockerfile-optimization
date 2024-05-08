# Base image
FROM node:8

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
RUN useradd -d /code -u 5000 nulldoot2k && \
    chown -R nulldoot2k:nulldoot2k /code

USER nulldoot2k

# Expose application port
EXPOSE 8080

# Define entrypoint
ENTRYPOINT ["npm", "run"]

# Define default command
CMD ["start"]
