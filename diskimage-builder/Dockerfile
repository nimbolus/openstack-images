FROM docker.io/ubuntu:24.04

RUN apt-get update \
    && apt-get install -y sudo \
    && groupadd -g 2000 builder \
    && useradd -u 2000 -g 2000 -m -s /bin/bash builder \
    && echo "builder ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/010_builder-nopasswd

RUN apt-get install -y --no-install-recommends python3-venv git \
    procps qemu-utils qemu-user-static squashfs-tools debootstrap gdisk kpartx dosfstools e2fsprogs \
    podman uidmap fuse-overlayfs

USER builder
WORKDIR /home/builder

COPY requirements.txt requirements.txt

RUN python3 -m venv dib \
    && dib/bin/pip install -U pip \
    && dib/bin/pip install -r requirements.txt \
    && echo "source \$HOME/dib/bin/activate" >> .bashrc
