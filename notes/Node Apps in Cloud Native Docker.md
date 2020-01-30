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
