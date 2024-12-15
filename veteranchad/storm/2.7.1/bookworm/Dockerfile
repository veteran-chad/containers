FROM docker.io/bitnami/minideb:bookworm

ARG STORM_VERSION=2.7.1
ARG DISTRO_NAME=apache-storm-${STORM_VERSION}

ENV STORM_CONF_DIR=/conf \
    STORM_DATA_DIR=/data \
    STORM_LOG_DIR=/logs

# Add a user with an explicit UID/GID and create necessary directories
RUN set -eux; \
    groupadd -r storm --gid=1000; \
    useradd -r -g storm --uid=1000 storm; \
    mkdir -p "$STORM_CONF_DIR" "$STORM_DATA_DIR" "$STORM_LOG_DIR"; \
    chown -R storm:storm "$STORM_CONF_DIR" "$STORM_DATA_DIR" "$STORM_LOG_DIR"``

RUN echo "${DISTRO_NAME} DISTRO_NAME"

RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y wget python3 &&  \
    apt-get clean && rm -rf /var/lib/apt/lists /var/cache/apt/archives


RUN wget https://downloads.apache.org/storm/${DISTRO_NAME}/${DISTRO_NAME}.tar.gz; \
    tar xvf ${DISTRO_NAME}.tar.gz; \
    rm -rf "${DISTRO_NAME}.tar.gz"; \
    chown -R storm:storm "${DISTRO_NAME}"

USER 1000

CMD ["/bin/bash", "-c", "while true; do sleep 3600; done"]