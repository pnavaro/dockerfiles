FROM python:3
LABEL maintainer="Matthieu Boileau <matthieu.boileau@math.unistra.fr>"

RUN apt-get update --fix-missing && \
    apt-get install -y \ 
    latexmk \
    texlive-lang-french \
    locales \
    vim && \
    apt-get --purge remove -y .\*-doc$ && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN sed -i 's/# fr_FR.UTF-8 UTF-8/fr_FR.UTF-8 UTF-8/' /etc/locale.gen  
RUN locale-gen fr_FR.UTF-8  
ENV LANG fr_FR.UTF-8  
ENV LANGUAGE fr_FR
ENV LC_ALL fr_FR.UTF-8  
RUN dpkg-reconfigure -f noninteractive locales

CMD /bin/bash
