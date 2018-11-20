FROM jupyter/minimal-notebook

# From Jupyter Project <jupyter@googlegroups.com>

LABEL maintainer="Matthieu Boileau <matthieu.boileau@math.unistra.fr>"

USER root

RUN apt-get update && apt-get -yq dist-upgrade \
 && apt-get install -yq --no-install-recommends \
    rsync \
    texlive-latex-recommended \
    texlive-fonts-recommended \
    texlive-lang-french \
    zip \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# PATH to pip executable
ENV PATH=~/.local/bin:$PATH

# ---
# Manual installation of pyproj due to https://github.com/jswhit/pyproj/issues/136
# May be removed when issue is closed
RUN pip install --no-cache-dir cython

WORKDIR /tmp
RUN git clone https://github.com/jswhit/pyproj.git && \
    cd pyproj && \
    python setup.py build && \
    python setup.py install
# ---

ADD requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

RUN python3 -m bash_kernel.install

# Switch back to NB_USER to avoid accidental container runs as root
USER $NB_USER
WORKDIR $HOME/work
