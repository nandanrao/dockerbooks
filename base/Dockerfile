FROM python:3.8-slim

ARG NB_USER="jupyter"
ARG NB_UID="1000"

ENV NB_USER=$NB_USER \
    NB_UID=$NB_UID

RUN useradd -ms /bin/bash -u $NB_UID $NB_USER
USER $NB_USER

ENV PATH "/home/${NB_USER}/.local/bin:${PATH}"

RUN pip install --user jupyter
RUN mkdir /home/jupyter/work
WORKDIR /home/jupyter/work
EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=*"]
