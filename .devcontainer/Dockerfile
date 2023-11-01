ARG PYTHON_MIN_VERSION="3"
FROM mcr.microsoft.com/devcontainers/python:${PYTHON_MIN_VERSION}

ENV DEBIAN_FRONTEND noninteractive
ENV TZ=Europe/Berlin
ENV APT_KEY_DONT_WARN_ON_DANGEROUS_USAGE=DontWarn

ENV REFRESHED_AT 2023-11-01
ENV CONFIGURATION_DIR_PATH supporting_files/configuration
ENV SCRIPTS_DIR_PATH supporting_files/scripts

# Add image configuration and scripts
ADD ${SCRIPTS_DIR_PATH}/post-create.sh /post-create.sh

# Time Zone
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# zsh and commitizen (cz) configurations
ARG USERNAME="vscode"
ARG USERHOME="/home/${USERNAME}"
COPY ${CONFIGURATION_DIR_PATH}/.zshrc ${USERHOME}/.zshrc
COPY ${CONFIGURATION_DIR_PATH}/.czrc ${USERHOME}/.czrc
RUN chown ${USERNAME}:${USERNAME} ${USERHOME}/.zshrc ${USERHOME}/.czrc \
    && chmod +x ${USERHOME}/.zshrc ${USERHOME}/.czrc
    
WORKDIR /usr/share/rtldev-middleware-python-sdk-demo
