FROM node:6-slim

ARG THELOUNGE_VERSION=2.4.0
ENV NODE_ENV production

ENV LOUNGE_HOME "/home/lounge/data"

RUN mkdir -p "${LOUNGE_HOME}"
VOLUME "${LOUNGE_HOME}"

# Install thelounge.
RUN npm install -g thelounge@${THELOUNGE_VERSION} && \
    npm cache clean

# Expose HTTP.
ENV PORT 9000
EXPOSE ${PORT}

COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh

CMD ["lounge", "start"]

ENTRYPOINT ["docker-entrypoint.sh"]
