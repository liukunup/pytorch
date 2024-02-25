# 基础镜像
ARG REGISTRY=nvcr.io
ARG OWNER=nvidia
ARG BASE_CONTAINER=$REGISTRY/$OWNER/cuda
ARG VERSION=12.0.1-cudnn8-runtime-ubuntu22.04
FROM $BASE_CONTAINER:$VERSION

# 作者信息
LABEL authors="LiuKun <liukunup@outlook.com>"

# 设置为非交互(即无需等待用户输入的提示)
ENV DEBIAN_FRONTEND=noninteractive

# 系统更新以及安装软件
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    vim \
    wget \
    git \
    curl \
    unzip && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# 默认的入口程序脚本
COPY images/entrypoint.sh /

# 默认入口程序
ENTRYPOINT ["/entrypoint.sh"]
