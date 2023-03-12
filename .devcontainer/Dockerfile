FROM jupyter/datascience-notebook

## install imagemagick
USER root
RUN conda install -c conda-forge imagemagick

## Install R libraries
USER ${NB_UID}

RUN pip install jupyterlab-link-share \
    && jupyter server extension disable nbclassic  

RUN R -e "install.packages(c('lobstr', 'pryr', 'gmp', 'float', 'mvtnorm', 'microbenchmark', 'SparseM', 'statmod', 'plot3D', 'Rlinsolve', 'animation'), dependencies=TRUE, repos='http://cran.rstudio.com/')" 
RUN R -e "remotes::install_github('coolbutuseless/uint8')"

