FROM debian:bookworm-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    bash curl unzip zip ca-certificates \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash dev && \
    echo "dev ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER dev

RUN curl -s 'https://get.sdkman.io' | bash

RUN bash -c "source $HOME/.sdkman/bin/sdkman-init.sh && sdk version && sdk install java && sdk install springboot"

ENV SDKMAN_DIR=/home/dev/.sdkman
ENV PATH=$SDKMAN_DIR/candidates/springboot/current/bin:$SDKMAN_DIR/candidates/java/current/bin:$PATH

CMD ["bash"]
