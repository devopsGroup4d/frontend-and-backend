FROM node:16-alpine


RUN mkdir -p /app && \
    addgroup -S appgroup && \
    adduser -S appuser -G appgroup && \
    chown -R appuser:appgroup /app


WORKDIR /app

# Set npm cache to a writable directory
ENV NPM_CONFIG_CACHE=/tmp/.npm

# Copy package files first for better layer caching
COPY --chown=appuser:appgroup package*.json package-lock.json ./

# Install dependencies with clean cache
RUN npm config set cache /tmp/.npm && \
    npm install --no-optional && \
    mkdir -p node_modules/.cache && \
    chmod -R 777 node_modules/.cache && \
    ls -l /app/node_modules

# Copy application files
COPY --chown=appuser:appgroup . .

# Verify installed packages and build
RUN npm list --depth=0 && \
    npm run build && \
    chmod -R +x node_modules/.bin

# Install serve globally (for production)
RUN npm install -g serve

EXPOSE 3000

# Use serve for production or npm start for development
CMD ["npm", "start"]
