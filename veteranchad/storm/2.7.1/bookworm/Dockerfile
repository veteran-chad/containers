FROM docker.io/bitnami/minideb:bookworm

RUN apt-get update && apt-get upgrade -y && \
    apt-get clean && rm -rf /var/lib/apt/lists /var/cache/apt/archives

USER 1001

CMD ["/bin/bash", "-c", "while true; do sleep 3600; done"]