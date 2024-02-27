# 基础镜像
ARG REGISTRY=quay.io
ARG OWNER=jupyter
ARG BASE_CONTAINER=$REGISTRY/$OWNER/scipy-notebook
ARG VERSION=latest
FROM $BASE_CONTAINER:$VERSION

# 作者信息
LABEL maintainer="LiuKun <liukunup@outlook.com>"

# Fix: https://github.com/hadolint/hadolint/wiki/DL4006
# Fix: https://github.com/koalaman/shellcheck/wiki/SC3014
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install PyTorch with pip (https://pytorch.org/get-started/locally/)
# Install Tensorflow with pip
# hadolint ignore=DL3013
RUN pip install --no-cache-dir --extra-index-url=https://pypi.nvidia.com --index-url 'https://download.pytorch.org/whl/cu116' \
    'torch' \
    'torchvision' \
    'torchaudio'  && \
    pip install --no-cache-dir tensorflow && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

# https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/docker-specialized.html#dockerfiles
ENV NVIDIA_VISIBLE_DEVICES all
ENV NVIDIA_DRIVER_CAPABILITIES compute,utility
