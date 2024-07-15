FROM nvcr.io/nvidia/cuda:12.5.1-cudnn-devel-ubuntu22.04

RUN apt update && apt -y install curl
RUN curl -sSf https://rye.astral.sh/get | RYE_INSTALL_OPTION="--yes" bash
RUN mkdir /workspace

COPY . /workspace
WORKDIR /workspace
RUN . ~/.profile && rye sync