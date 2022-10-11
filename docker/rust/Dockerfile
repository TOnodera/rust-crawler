FROM rust:latest
RUN useradd -m -u 1000 -s /bin/bash rust 
RUN rustup component add rustfmt

# chrome
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add && \
    echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' | tee /etc/apt/sources.list.d/google-chrome.list && \
    apt-get update && \
    apt-get install -y google-chrome-stable

# chromedriver
RUN curl -O https://chromedriver.storage.googleapis.com/106.0.5249.61/chromedriver_linux64.zip \
    && unzip chromedriver_linux64.zip \
    && mv chromedriver /usr/local/bin/

# clean up
RUN apt-get -y clean && \
    rm -rf /var/lib/apt/lists/*

USER rust