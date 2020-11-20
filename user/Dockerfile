ARG BASE
FROM dockerbooks/${BASE}

ARG USERID
ARG GROUPID

RUN addgroup --gid $GROUPID jupyter
RUN useradd -lms /bin/bash -u $USERID -g $GROUPID jupyter

USER jupyter
ENV HOME "/home/jupyter"
ENV PYTHONUSERBASE "$HOME/.local"
ENV PATH "${PYTHONUSERBASE}/bin:${PATH}"

RUN mkdir /home/jupyter/work
WORKDIR /home/jupyter/work


# Set all home files, including .local
# and .cache to group read/write/executable
# so users can use local pip if in group jupyter
USER root
RUN chmod -R 774 /home/jupyter && \
        setfacl -R -d -m u::rwX -m g::rwX /home/jupyter


# make
USER jupyter
RUN pip install --user jupyter
