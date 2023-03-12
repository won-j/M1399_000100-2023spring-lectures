FROM jupyter/datascience-notebook

## install imagemagick
USER root

RUN conda install -c conda-forge imagemagick

ENV SHELL=/bin/bash

# Hack for controlling how chromium works with no-sandbox and allow-downloads
RUN mkdir -p /home/jovyan/.jupyter
#COPY .devcontainer/jupyter_nbconvert_config.py /home/jovyan/.jupyter/jupyter_nbconvert_config.py
COPY .devcontainer/jupyter_lab_config.py /home/jovyan/.jupyter/jupyter_lab_config.py
#COPY .devcontainer/jupyter_server_config.json /home/jovyan/.jupyter/jupyter_server_config.json

RUN fix-permissions /home/jovyan/.jupyter

## Install R libraries
USER ${NB_UID}

#RUN jupyter server extension disable nbclassic  

RUN R -e "install.packages(c('lobstr', 'pryr', 'gmp', 'float', 'mvtnorm', 'microbenchmark', 'SparseM', 'statmod', 'plot3D', 'Rlinsolve', 'animation'), dependencies=TRUE, repos='http://cran.rstudio.com/')" 
RUN R -e "remotes::install_github('coolbutuseless/uint8')"

