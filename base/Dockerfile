FROM python:3.8-slim

RUN useradd -ms /bin/bash -u 1000 jupyter

RUN mkdir /srv/users
RUN chown jupyter:users /srv/users
RUN chmod -R 774 /srv/users

ENV PYTHONUSERBASE "/srv/users"
ENV PATH "${PYTHONUSERBASE}/bin:${PATH}"

USER jupyter

RUN pip install --user jupyter
RUN mkdir /home/jupyter/work
WORKDIR /home/jupyter/work
EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=*"]
