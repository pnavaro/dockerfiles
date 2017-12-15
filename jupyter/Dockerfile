FROM jupyter/minimal-notebook

# From Jupyter Project <jupyter@googlegroups.com>

LABEL maintainer="Matthieu Boileau <matthieu.boileau@math.unistra.fr>"

USER root

RUN apt-get update && apt-get -yq dist-upgrade \
 && apt-get install -yq --no-install-recommends \
    rsync \
    texlive-latex-recommended \
    texlive-fonts-recommended \
    zip \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /tmp
RUN wget https://bootstrap.pypa.io/get-pip.py && \
    python3 get-pip.py

RUN pip install --no-cache-dir latex geopandas folium seaborn bookbook

# Switch back to NB_USER to avoid accidental container runs as root
USER $NB_USER
WORKDIR $HOME/work
