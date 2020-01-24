FROM python:3.6

RUN pip install jupyter
RUN useradd -ms /bin/bash jupyter

# ---------------------
# Install R
# ---------------------
RUN apt update && apt install --yes software-properties-common
RUN apt-key adv --keyserver keys.gnupg.net --recv-key 'E19F5F87128899B192B1A2C2AD5F960A256A04AF'
RUN add-apt-repository 'deb http://cloud.r-project.org/bin/linux/debian stretch-cran35/'
RUN apt update && apt install --yes --install-recommends r-base r-base-dev

# ---------------------
# Install R packages
# ---------------------
USER jupyter

RUN mkdir ~/R && \
    mkdir ~/R/x86_64-pc-linux-gnu-library && \
    mkdir ~/R/x86_64-pc-linux-gnu-library/3.6

RUN Rscript -e "install.packages('IRkernel')"
RUN Rscript -e "IRkernel::installspec()"
RUN Rscript -e "install.packages(c( \
        'ggplot2', \
        'highcharter', \
        'plotly', \
        'googleVis', \
        'pheatmap', \
        'RColorBrewer', \
        'ggmap', \
        'plotrix', \
        'plot3D', \
        'igraph', \
        'quantmod', \
        'forecast', \
        'fanplot', \
        'corrplot', \
        'shiny' \
        ))"

# ---------------------
# Python Packages
# ---------------------

USER root

RUN apt update && apt install --yes graphviz

RUN pip install  \
        matplotlib==3.1.1 \
        seaborn==0.9.0 \
        pandas==0.25.1 \
        scikit-learn==0.21.3 \
        requests==2.22.0 \
        beautifulsoup4==4.8.0 \
        pydotplus==2.0.2 \
        graphviz==0.13 \
        Keras==2.3.0 \
        matplotlib==3.1.1 \
        seaborn==0.9.0 \
        ggplot==0.11.5 \
        bokeh==1.3.4 \
        pygal==2.4.0 \
        plotly==4.1.1 \
        gleam==0.1.2 \
        missingno==0.4.2 \
        pandas-highcharts==0.5.2 \
        gensim==3.8.1 \
        nltk==3.4.5 \
        spacy==2.1.8 \
        Cython==0.29.13 \
        ipywidgets==7.5.1 \
        html5lib==1.0.1 \
        pyspark==2.4.4 \
        rpy2==3.2.0 \
        https://github.com/explosion/spacy-models/releases/download/en_core_web_md-2.1.0/en_core_web_md-2.1.0.tar.gz

USER jupyter
RUN mkdir /home/jupyter/work
WORKDIR /home/jupyter/work
EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=*"]
