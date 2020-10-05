FROM node as builder

ARG NPM_REGISTRY=https://registry.npmjs.org/
# This is how we can control what version is being published, as 
# Settings does not leverage Releases.
ARG COMMIT_HASH=fc6ded2f3e24ab5765d3b8db9cbef3883c567bae

ADD https://github.com/probot/settings/archive/${COMMIT_HASH}.zip /

RUN apt-get update && \
    apt-get install -y unzip --no-install-recommends && \
    unzip ${COMMIT_HASH}.zip -d /${COMMIT_HASH} && \
    mv ${COMMIT_HASH}/settings-${COMMIT_HASH} /settings_probot && \
    cd settings_probot && \
    npm config set registry ${NPM_REGISTRY} && \
    npm install;

FROM node as probotPrep
ARG NPM_REGISTRY
COPY --from=builder settings_probot/ ./settings_probot
WORKDIR /settings_probot
RUN npm config set registry ${NPM_REGISTRY} && \
    npm install probot

FROM node:slim as app
COPY --from=probotPrep settings_probot/ /settings_probot
VOLUME ["/settings_probot"]
WORKDIR /settings_probot
USER node
ENTRYPOINT  [ "npm", "run", "start" ]
