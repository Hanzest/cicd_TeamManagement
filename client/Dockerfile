ARG BUN_VERSION=1.1.42

FROM oven/bun:${BUN_VERSION}-alpine

WORKDIR /usr/src/app

# Copy package files first
COPY package.json bun.lock ./

# Install all dependencies (including devDependencies)
RUN bun install

# Copy the rest of the application
COPY . .

# Use development node environment for dev server
ENV NODE_ENV=development

EXPOSE 5173

CMD ["bun", "run", "dev"]