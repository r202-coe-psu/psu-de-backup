FROM debian:sid

# comment this line if you are outside PSU
RUN echo 'deb http://mirror.psu.ac.th/debian/ sid main contrib non-free non-free-firmware' > /etc/apt/sources.list


RUN apt-get update && apt-get install -y \
    python3-pip \
    python3-wheel \
    python3-venv \
    sudo \
    openssh-server


RUN useradd -m -s /bin/bash -d /home/psu psu
RUN usermod -aG sudo psu
RUN echo 'psu:coe' | chpasswd


RUN python3 -m venv /venv

RUN . /venv/bin/activate && pip install poetry gunicorn

WORKDIR /app
COPY code /app

RUN . /venv/bin/activate \
    && poetry config virtualenvs.create false \
    && poetry install --no-interaction --only main

CMD ["/usr/sbin/sshd", "-D"]