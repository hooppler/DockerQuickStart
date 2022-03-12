#FROM node:12-alpine
#
#LABEL author="Aleksandar Stojimirovic"
#
#ENV NODE_ENV=production
#ENV PORT=3000
#
#WORKDIR /var/www
#
#COPY . ./
#
#EXPOSE $PORT

FROM node:12-alpine AS app-base
WORKDIR /app
COPY . ./

