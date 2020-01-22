FROM node:10-slim as prod
ENV NODE_ENV=production
COPY package*.json ./
RUN npm install --only=production && npm cache clean --force
COPY . .
CMD ["node", "./bin/www"]
# docker build -t multistage --target prod .

FROM prod as dev
ENV NODE_ENV=development
RUN npm install --only=development && npm cache clean --force
CMD ["nodemon",  "./bin/www", "--inspect=0.0.0.0:9229"]

FROM dev as test
ENV NODE_ENV=development
CMD ["npm", "test"]
# RUN npm test(これで一緒にテスト勝手に走る。↑は自分でやる。場所も動かせる。例えばprodのとこでもOK)

# docker build -t multistage --target prod . && docker run multistage
# docker build -t multistage:dev --target dev . && docker run --init -p 3000:3000 multistage:dev
# docker build -t multistage:test --target test . && docker run --init multistage:test