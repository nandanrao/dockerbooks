FROM dockerbooks/base:3.7

USER root

RUN apt-get update && apt-get install --yes \
        graphviz \
        gcc

USER $NB_USER

RUN pip install  --user \
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
