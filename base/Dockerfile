FROM python:3.8-slim

RUN useradd -ms /bin/bash -u 1000 jupyter

RUN apt-get update && apt-get install --yes \
        acl

USER jupyter
ENV HOME "/home/jupyter"
ENV PYTHONUSERBASE "$HOME/.local"
ENV PATH "${PYTHONUSERBASE}/bin:${PATH}"

RUN pip install --user jupyter
RUN mkdir /home/jupyter/work
WORKDIR /home/jupyter/work


# Set all home files, including .local
# and .cache to group read/write/executable
# so users can use local pip if in group jupyter
USER root
RUN chmod -R 774 /home/jupyter && \
        setfacl -R -d -m u::rwX -m g::rwX /home/jupyter


USER jupyter
EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=*"]
