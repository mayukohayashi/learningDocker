## Dockerfile Node Basics

- COPY, not ADD (ADD has lots of functions)
- npm/yarn install during build (whichever)
- CMD node, not npm 
- WORKDIR not RUN mkdir
    - unless you need chown

