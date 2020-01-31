## Cloud Native App Guidelines

- Follow 12factor.net principle, especiall [https://12factor.net/](https://12factor.net/)
  1. use Environment Variable for config
  2. Log to stdout/stderr
  3. pin all versions, even npm
  4. Gracefully exit SIGTERM/INIT
- Create a .dockerignore

### 12 Factor = Container Happiness

- Heroku wrote a highly respected guide to creating distributed apps
- Twelve factors to consider when developing or designing distrubuted apps
- Containers are almost always distributed apps
- Good news: you get many of these by using Docker

### 12 Factor: Config

- https://12factor.net/config
- Store environment config in Environment Variables(env vars)
- Docker & compose are great this with multiple options
- Old apps: user CMD or ENTRYPOINT script with envsubst to pass env vars into conf files

### 12 Factor: Logs

- 12factor.net/logs
- Apps shouldnt route or transport logs to anything but stdout/stderr
- console.log() works
- Winston/Bunyan/Morgan: use levels to control verbosity
- Winston transport: "Console

### .dockerignore

- Prevent bloat and unneeded files
  - .git/
  - node_modules/
  - npm-debug
  - docker-compose\*.yml
- Not needed but useful in image
  - Dockerfile
  - README.md

### Migrating Traditional Apps (Assiginment4)

- "Transitional App" = Pre-Docker App
- Take a typical Node app and "migrate"
-
