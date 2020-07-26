FROM node

# install some packages to use electron
RUN apt-get update \
    && apt-get -y install libgtkextra-dev libgconf2-dev libnss3 libasound2 libxtst-dev libxss1 libgtk-3-0 \
    && npm install -g npm @vue/cli

RUN apt-get update \
    && apt-get install -y curl sudo

# 日本語が使えるようにする
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
    && apt-get install -y locales
RUN locale-gen ja_JP.UTF-8

ENV LANG ja_JP.UTF-8
ENV LC_CTYPE ja_JP.UTF-8
RUN localedef -f UTF-8 -i ja_JP ja_JP.utf8

# install yarn
RUN curl -o- -L https://yarnpkg.com/install.sh | bash \
    && export PATH="$PATH:`yarn global bin`"

# add user
ARG DOCKER_UID=501
ARG DOCKER_USER=docker
ARG DOCKER_PASSWORD=docker
RUN useradd -m -u ${DOCKER_UID} -G sudo ${DOCKER_USER} \
    && echo ${DOCKER_USER}:${DOCKER_PASSWORD} | chpasswd

# set workdir
WORKDIR /home/${DOCKER_USER}/app

# install electron
RUN yarn -D add electron

#set user
USER ${DOCKER_USER}

# not to use shared memory
ENV QT_X11_NO_MITSHM=1
