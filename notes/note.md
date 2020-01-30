## Dockerfile Node Basics
- COPY, not ADD (ADD has lots of functions)
- npm/yarn install during build (whichever)
- CMD node, not npm
- WORKDIR not RUN mkdir
    - unless you need chown


## FROM BASE IMAGE GUIDELINES
- Don't use: latest Tag
- LTS!long term stable
- all default stemming from Debian-based image
- start with Debian ig migrating
- Move to Alpine later (minimal)
- Dont use: slim
- dont use: onbuild


## WHEN to use alpine images
- Alpin is "small" and "sec focused"
- Debian/Ubuntu are smaller now too
- ~100mb space isnt significant
- Alpine has its own issues
- Alpine CVE scanning fails
- Enterprise may require CentOS or Ubuntu/Debian

## Making Images Efficiently
- Pick proper FROM (check well! what version?)
- Line order matters (top to bottom, cache busting)
- COPY twice (コピー全部してからnpm installとかcacheやばいで)
    1. copy only the package and lock fils
    2. run npm install
    3. copy everything else!
- One apt-get per Dockerfile / apt-get update cache prob


# Controlling The Node Process In Containers

## Node process management in containers
- No need for nodemon or pm2 on server (we will use nodemon in dev for file watch later)
- Docker manages app start, stop, restart, health check
- Node multi-thread: Docker manages multiple "replicas"
- One npm/node problem; they don't listen for proper shutdown signal for default


## The truth about the PID 1 problem
- PID 1 (Process Identifier) is the first process in a system (or container) (AKA init)
- Init process in a container has two jobs
    1. reap zombie process
    2. pass signals to sub-processes
- Zombie not a big Node issue
- Focus on proper Node shutdown

## Proper CMD for Healthy Shutdown
- Docker uses Linux signals to stop app (SIGINT / SIGTERM / SIGKILL)
- SIGINT / SIGTERM allow graceful stop
- npm doesn't respond to SIGINT / SIGTERM
- node doesn't respond by default, but can with code
- Docker provides a init PID 1 replacement option

## Proper Node Shutdown Options
- Temp: Use --init to fix ctrl-c for now
- Workaround: add tini to your image
- Production: your app captures SGINT for proper exit

### example commands
- Run any node app with --init to handle signals (temp solution)
    > docker run --init -d nodeapp
    > ENTRYPOINT ["/sbin/tini", "--"]
    > CMD ["node", "./bin.www"]
- Use JS snippet to properly capture signals (production solution)
    > ./sample-gracefully-shutdown/sample.js