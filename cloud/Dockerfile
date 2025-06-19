FROM debian:sid

RUN apt-get update && apt-get install -y \
    git \
    python3-dev \
    python3-pip \
    python3-wheel \
    python3-venv \
    ansible 

COPY code /app

CMD ["tail", "-f", "/dev/null"]