FROM debian:stable-slim

RUN apt update
RUN apt install -y curl wget unzip sudo git ca-certificates tar bash sqlite3 gnupg2 python3 python3-pip zip sed
RUN curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash - \
    && sudo apt-get install -y nodejs
RUN curl -sL https://github.com/shyiko/jabba/raw/master/install.sh | bash && . ~/.jabba/jabba.sh \
    && jabba install graalvm-ce-java16@21.1.0 \
    && jabba use graalvm-ce-java16@21.1.0
RUN wget https://golang.org/dl/go1.17.1.linux-amd64.tar.gz \
    && tar -C /usr/local -xzf go1.17.1.linux-amd64.tar.gz \
    && export PATH=$PATH:/usr/local/go/bin
RUN wget -O sdk.install.sh "https://get.sdkman.io" \
    && bash sdk.install.sh \
    && source "/root/.sdkman/bin/sdkman-init.sh" \
    && sdk install kotlin
RUN wget https://raw.githubusercontent.com/ILoveCatto/VsQBdVzAEu-docker1/main/Code-Server-Ultimate/entrypoint.sh
RUN curl -fsSL https://code-server.dev/install.sh | sh
USER container
ENV  USER=container HOME=/home/container

WORKDIR /home/container

CMD ["/bin/bash", "/entrypoint.sh"]