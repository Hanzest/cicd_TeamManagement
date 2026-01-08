ARG BUN_VERSION=1.1.42

FROM oven/bun:${BUN_VERSION}-alpine

WORKDIR /usr/src/app

# Install curl for healthchecks
RUN apk add --no-cache curl

# Copy package files first
COPY package.json bun.lock* ./

# Install dependencies
RUN bun install

# Copy the rest of the application
COPY . .

# Create public directory if it doesn't exist
RUN mkdir -p public

# Use development node environment
ENV NODE_ENV=development
ENV PORT=3000

# Expose the backend port
EXPOSE 3000

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=40s --retries=3 \
  CMD curl -f http://localhost:3000/api/csrf-token || exit 1

# Start the server
CMD ["bun", "run", "server"]