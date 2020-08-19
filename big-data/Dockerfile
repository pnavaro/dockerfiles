FROM jupyter/pyspark-notebook

MAINTAINER Pierre Navaro <pierre.navaro@univ-rennes2.fr>

USER root
RUN apt-get update && apt-get install -yq git

USER $NB_USER
RUN git clone https://github.com/pnavaro/big-data.git
RUN conda env create --quiet -f big-data/environment.yml && \
    conda run -n big-data python -m ipykernel install --user --name big-data && \
    conda clean --all -f -y && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER
