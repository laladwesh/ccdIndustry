FROM node:20-alpine AS base
WORKDIR /app
FROM base AS dependencies
COPY package*.json ./
# Install app dependencies using 'npm ci' which is faster and more reliable for builds
RUN npm ci
FROM dependencies AS build
WORKDIR /app
COPY . .
FROM base AS production
WORKDIR /app

COPY --from=build /app/ .

EXPOSE 5002

CMD [ "npm", "start" ]