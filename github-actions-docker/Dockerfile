# ---------- Stage 1: Build ----------
FROM node:20 AS builder

WORKDIR /app

# Copy only dependencies first for caching
COPY package*.json ./
RUN npm install --production

# Copy app code
COPY . .

# ---------- Stage 2: Production ----------
FROM node:20-alpine

WORKDIR /app

# Copy built app from builder
COPY --from=builder /app /app

EXPOSE 3000

CMD ["node", "app.js"]
