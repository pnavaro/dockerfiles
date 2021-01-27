FROM ubuntu:18.04

LABEL maintainer="Pierre Navaro <navaro@math.cnrs.fr>"

ENV DEBIAN_FRONTEND=noninteractive
ENV REFRESHED_AT 2016-07-01

RUN apt-get update --fix-missing && \
    apt-get install -yq \ 
    make locales \
    pandoc \
    latexmk texlive-xetex texlive-lang-french texlive-fonts-extra \
    python3-dev python3-wheel python3-venv python3-pip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN useradd -m -s /bin/bash euler
ENV HOME /home/euler
RUN chown -R euler:euler /home/euler
USER euler
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8
WORKDIR $HOME
CMD /bin/bash
