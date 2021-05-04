FROM dockerbooks/base

USER root

RUN apt-get update && apt-get install --yes \
        graphviz \
        gcc \
        g++ \
        git \
        libspatialindex-dev

RUN pip install \
        numba \
        pandas \
        matplotlib \
        seaborn \
        scikit-learn \
        Cython \
        pydotplus \
        graphviz \
        ipywidgets \
        psutil
