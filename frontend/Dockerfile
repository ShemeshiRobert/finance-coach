# frontend/Dockerfile

# --- Build Stage ---
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# --- Serve Stage ---
FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
# If using React Router, handle client-side routing:
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80