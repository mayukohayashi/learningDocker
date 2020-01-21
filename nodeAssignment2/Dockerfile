# fill in the blanks to dockerize this node app
FROM node:10.15-alpine

EXPOSE 3000

RUN apk add --no-cache tini

WORKDIR /usr/src/app

COPY package.json package-lock.json* ./

RUN npm install && npm cache clean --force

COPY . .

ENTRYPOINT ["/sbin/tini", "--"]

CMD ["node", "app.js"]
