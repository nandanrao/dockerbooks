FROM python:3.11-slim-buster

RUN apt-get update && apt-get install --yes \
        acl

EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=*"]
