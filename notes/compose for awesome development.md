## COMPOSE FOR AWESOME DEVELOPMENT

### compose project tips: Do's

- cd ./compose-tips
- Do use docker-compose got local dev
- Do use v2 format for local dev
- v2 only: depends_on, hardware specific
- Do study compose file and CLI features

### Compose Project Tips; Don't

- Unnecessary; "alias" & "container_name"
- Legacy: "expose" & "Links"
- No need to set defaults

### Bind-Mounting Code

- Don't use host file paths
- Don't bind-mount databases
- For local dev only? do not copy in code
- DDforWin needs drive perms
- Perms: Linux != Windows

### node_modules in Images

- Problem: we shouldn't build images with node_modules from host
  - Example: node-gyp
- Solution; add node_modules\ to .dockerignore
- Lets do this to ./sample-sails

### node_modules in Bind-mounts

- Problem: we cant bind-mount node_modules content from host on macOS/Windows(different arch)
- Two potential Solutions:
  - Never use npm i on host, run npm i in compose
  - Move modules in image, hide modules from host

### node_modules in Bind-Mounts

- Solution 1, simple but less flexible:
  - You cant docker-compose up until you've used docker-compose run
  - node_modules on host is now only usable container
- Solution 2, more setup but flexible:
  - move node_modules up a directory in Dockerfile
  - Use empty volume to hide node_modules on bind-mount

### NPM, Yarn, and Other Tools in Compose
