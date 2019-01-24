FROM ubuntu:18.04
LABEL maintainer="Matthieu Boileau <matthieu.boileau@math.unistra.fr>"

RUN echo "Europe/Paris" > /etc/timezone
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update --fix-missing && \
    apt-get install -y \ 
    latexmk \
    make \
    texlive-lang-french \
    vim \
    tzdata \
    locales && \
    apt-get --purge remove -y .\*-doc$ && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN sed -i 's/# fr_FR.UTF-8 UTF-8/fr_FR.UTF-8 UTF-8/' /etc/locale.gen  
RUN locale-gen fr_FR.UTF-8  
ENV LANG fr_FR.UTF-8  
ENV LANGUAGE fr_FR
ENV LC_ALL fr_FR.UTF-8  
RUN dpkg-reconfigure -f noninteractive locales
RUN echo "Europe/Paris" > /etc/timezone
RUN dpkg-reconfigure -f noninteractive tzdata

RUN apt-get update && \
    apt-get install -y \ 
    texlive-bibtex-extra \
    texlive-science \
    texlive-latex-extra && \
    apt-get --purge remove -y .\*-doc$ && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN useradd -ms /bin/bash latex
USER latex
WORKDIR /home/latex

USER root
CMD /bin/bash
