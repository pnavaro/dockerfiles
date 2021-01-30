FROM ubuntu:20.04

MAINTAINER Pierre Navaro <navaro@math.cnrs.fr>

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get -yq dist-upgrade \
  && apt-get install -yq --no-install-recommends sudo apt-utils\
  && apt-get install -yq --no-install-recommends \
      ca-certificates build-essential git cmake g++ gfortran \
      liblapack-dev  libsuitesparse-dev \
      libopenmpi-dev openmpi-bin libhdf5-openmpi-dev \
      libfftw3-dev libopenblas-dev doxygen graphviz ghostscript \
      latexmk texlive-xetex texlive-lang-french texlive-fonts-extra
