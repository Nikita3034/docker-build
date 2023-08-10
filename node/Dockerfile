FROM node:18.13

# Install dependencies
RUN apt-get update && apt-get clean && rm -rf /var/lib/apt/lists/*

# Expose port 3000
EXPOSE 3000

# Set the user to non-root user "node"
USER node

# Set working directory
WORKDIR /var/www