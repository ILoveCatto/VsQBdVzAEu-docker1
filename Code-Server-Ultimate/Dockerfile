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
USER container
ENV  USER=container HOME=/home/container

WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh

CMD ["/bin/bash", "/entrypoint.sh"]