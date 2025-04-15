# Use minimal Node.js base image
FROM node:20-alpine

# Create app directory
WORKDIR /usr/src/app

# Copy package files and install
COPY package*.json ./
RUN npm install

# Copy the app code
COPY . .

# Create a non-root user and use it
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser

# Expose the app port
EXPOSE 3000

# Run the app
CMD ["node", "index.js"]
