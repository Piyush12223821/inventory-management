# client/Dockerfile

# Step 1: Build the Next.js app
FROM node:18 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Build the production version of the Next.js app
RUN npm run build

# Step 2: Use a lightweight image for production
FROM node:18-alpine AS runner

WORKDIR /app

# Copy only necessary files
COPY --from=builder /app ./

EXPOSE 3000

# Start the Next.js production server
CMD ["npm", "start"]
