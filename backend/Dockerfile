FROM node:16-alpine

# Set npm cache to a writable directory
ENV NPM_CONFIG_CACHE=/tmp/.npm

WORKDIR /app

# Copy package files first for better layer caching
COPY package*.json package-lock.json ./

# Install dependencies with clean cache
RUN npm config set cache /tmp/.npm && \
    npm install --no-optional && \
    ls -l /app/node_modules

# Copy application files
COPY . .

# Verify installed packages
RUN npm list --depth=0

EXPOSE 3001

CMD ["npm", "start"]
