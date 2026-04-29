# React frontend
FROM node:14-alpine

WORKDIR /app

# SECURITY ISSUE: Outdated base image (node:14 is EOL - CVE-2023-46809, CVE-2024-21892)
# Should be node:20-alpine

COPY package*.json ./
RUN npm ci --only=production

COPY . .
RUN npm run build

FROM nginx:1.21-alpine
# SECURITY ISSUE: nginx:1.21-alpine is outdated - multiple CVEs
# Should be nginx:1.25-alpine
COPY --from=0 /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
