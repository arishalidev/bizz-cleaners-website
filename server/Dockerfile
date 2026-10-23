FROM node:alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM node:alpine
WORKDIR /app
COPY package*.json ./
ENV NODE_ENV=production
RUN npm ci
COPY --from=build /app/dist ./dist
CMD ["node", "dist/index.js"]