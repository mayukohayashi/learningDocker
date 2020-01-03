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
