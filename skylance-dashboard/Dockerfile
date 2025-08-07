# Step 1: Build the React app
FROM node:20-alpine as builder

WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

# Step 2: Serve the static files using nginx
FROM nginx:alpine

COPY --from=builder /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]