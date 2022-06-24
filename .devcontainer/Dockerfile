# *********** Base python image *********************
FROM python:3.9 AS python-base

# Install packages needed for Python dependencies
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install \
    rsync \
    zip \
    unzip \
    strace \
    gdb \
    python3-dbg \
    dumb-init \
    nano \
    vim \
    libgeos++-dev \
    libgeos-doc \
    sqlite3 \
    && rm -rf /var/lib/apt/lists/*

# Install proj
RUN wget https://download.osgeo.org/proj/proj-8.2.1.tar.gz -O ./proj.tgz && \
    tar xvf ./proj.tgz && \
    cd ./proj-8.2.1 && \
    ./configure && \
    make -j5 install && \ 
    cd .. && \
    rm -rf proj-8.2.1 proj.tgz
ENV LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/lib"

# Poetry
RUN curl -sSL https://install.python-poetry.org | python

# VSCode support - creation of user, common packages etc
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN bash -c "$(curl -fsSL "https://raw.githubusercontent.com/microsoft/vscode-dev-containers/v0.238.1/script-library/common-debian.sh")" -- "true" "$USERNAME" "$USER_UID" "$USER_GID" "false"  \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/*
