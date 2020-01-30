## Multi-stage builds
- New feature in 17.06(mid2017)
- Build multiple images from one file
- Those images can FROM each other
- COPY files between them
- Space + security benefits
- Great for "artifact only"
- Great for dev + test + prod

1. FROM node as prod
2. ENV NODE_ENV=production
3. COPY package*.json ./
4. RUN npm install && npm cache clean --force
5. COPY . .
6. CMD ["node", "./bin/www"]
7. FROM prof as dev
8. ENV NODE_ENV=development
9. CMD ["nodemon", "./bin/www", "--inspect=0.0.0:9229"]

- To build dev image from dev stage
  > docker build -t myapp .
- To build prod image from prod stage
  > docker build -t myapp:prod --target prod .

## More Multi-stage
- Add a test stage that runs npm test
- Have CI build --target test stage before building prod
- Add npm install --only=development to dev stage
- Dont COPY into dev stage

