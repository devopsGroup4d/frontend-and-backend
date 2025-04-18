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

# Verify installed packages and build
RUN npm list --depth=0 && \
    npm run build && \
    chmod -R +x node_modules/.bin

# Install serve globally (for production)
RUN npm install -g serve

EXPOSE 3000

# Use serve for production or npm start for development
CMD ["npm", "start"]
