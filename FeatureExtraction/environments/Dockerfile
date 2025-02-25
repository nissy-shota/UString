ARG BASE_IMAGE=nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04
FROM ${BASE_IMAGE}

ARG PROJECT_NAME=UString
ARG USER_NAME=ShotaNishiyama
ARG PYTHON_VERSION=3.7
ARG APPLICATION_DIRECTORY=/home/${USER_NAME}/${PROJECT_NAME}

ENV DEBIAN_FRONTEND="noninteractive" \
    LC_ALL="C.UTF-8" \
    LANG="C.UTF-8" \
    PYTHONPATH=${APPLICATION_DIRECTORY}

# Following is needed to install python 3.7
RUN apt update && apt install --no-install-recommends -y software-properties-common 
RUN add-apt-repository ppa:deadsnakes/ppa

RUN apt update
RUN apt install --no-install-recommends -y \
    gcc \
    git curl make ssh openssh-client \
    python${PYTHON_VERSION} python3-pip \
    python3.7-dev \
    ffmpeg \
    libsm6 \
    libxext6 \
    g++
# Following is needed to swtich default python3 version
# For detail, please check following link https://unix.stackexchange.com/questions/410579/change-the-python3-default-version-in-ubuntu
RUN update-alternatives --install /usr/bin/python3 python3 /usr/bin/python${PYTHON_VERSION} 1 \
    && update-alternatives --set python3 /usr/bin/python${PYTHON_VERSION}

RUN apt-get install -y python-setuptools
RUN pip3 install -U setuptools
RUN pip3 install --upgrade pip
RUN pip3 install poetry

## for develop
RUN apt install --no-install-recommends -y \
    bash-completion
# Add user. Without this, following process is executed as admin. 
RUN useradd -ms /bin/sh ${USER_NAME}
USER ${USER_NAME}

WORKDIR ${APPLICATION_DIRECTORY}
# Create virtual environments inside of project.
RUN poetry config virtualenvs.in-project true
