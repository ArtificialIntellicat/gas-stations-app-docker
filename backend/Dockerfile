# Use the official Node.js image.
FROM node:14

# Create and change to the app directory.
WORKDIR /usr/src/app

# Install build tools
RUN apt-get update && apt-get install -y python3 make g++ && rm -rf /var/lib/apt/lists/*

# Copy application dependency manifests to the container image.
COPY package*.json ./

# Install dependencies.
RUN npm install

# Rebuild SQLite3 within the container
RUN npm rebuild sqlite3

# Copy local code to the container image.
COPY . .

# Run the web service on container startup.
CMD ["node", "server.js"]

# Expose port 3000
EXPOSE 3000
