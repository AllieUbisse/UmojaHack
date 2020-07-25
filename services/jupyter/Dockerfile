FROM jupyter/scipy-notebook

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8

USER root

RUN apt-get update --fix-missing && apt-get install -y \
    byobu \
    ca-certificates \
    curl \
    git-core \
    htop \
    unzip \
    wget \
    gcc \
    libpq-dev \
    python-dev \
    python3-dev \
    python3-llvmlite \
    build-essential \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*


ENV PATH /opt/conda/bin:$PATH
# update conda
RUN conda update -n base conda
RUN conda clean -tipsy
# conda stuff
RUN conda install py-xgboost

RUN pip install --upgrade pip
# seems 2 versions of numpy are installed. This is a fix
RUN pip uninstall -y numpy; pip uninstall -y numpy;pip uninstall -y numpy
RUN pip --no-cache-dir install -U \
    jupyter \
    jupyterlab \
    numpy \
    pandas \
    scikit-learn \
    seaborn \
    sqlalchemy \
    psycopg2-binary \
    pyarrow

# non core
RUN pip --no-cache-dir install -U \
    tqdm \
    jupyter_nbextensions_configurator \
    jupyter_contrib_nbextensions \
    scikit-optimize \
    imbalanced-learn \
    category_encoders



USER jovyan
WORKDIR /home/jovyan/
## if rebulding notebook need to delete old config
RUN rm -rf /home/jovyan/.jupyter
## install extentions
RUN jupyter contrib nbextension install --user
RUN jupyter nbextensions_configurator enable --user
#
RUN jupyter notebook --generate-config