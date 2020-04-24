FROM dockerbooks/base

USER root

RUN apt-get update && apt-get install --yes \
        graphviz \
        gcc

USER jupyter

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
