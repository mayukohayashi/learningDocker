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

### node?modules in Images

- Problem: we shoundt build images with node_modules from host
  - Example: node-gyp
- Solution; add node_modules\ to .dockerignore
- Lets do this to ./sample-sails
