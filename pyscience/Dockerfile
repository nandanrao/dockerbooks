from nandanrao/base-notebook

USER root

RUN apt-get update && apt-get install --yes graphviz

USER $NB_USER

RUN pip install  --user \
        matplotlib \
        seaborn \
        pandas \
        scikit-learn \
        Cython \
        requests \
        pydotplus \
        graphviz \
        gensim \
        nltk \
        spacy \
        ipywidgets \
        rpy2
