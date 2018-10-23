# Joblocal - Docker Base Images

This repository holds all joblocal base images.

The images are used by our CI tools (prefixed 'build') and as base images for our services.

## Build

[Docker Hub](https://hub.docker.com) is setup to build the images automatically on a master push.

## Images

### Build Images
- [node/build/10.8.0](https://hub.docker.com/r/joblocal/base-build-node-awscli/)
- [node/build/10.12.0](https://hub.docker.com/r/joblocal/base-build-node-awscli/)
- [php/build/alpine-3.7](https://hub.docker.com/r/joblocal/base-build/)

### Base Images
- [php/app/alpine-3.7](https://hub.docker.com/r/joblocal/base-app/)
- [php/worker/alpine-3.7](https://hub.docker.com/r/joblocal/base-worker/)
