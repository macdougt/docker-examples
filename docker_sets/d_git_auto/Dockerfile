ARG base_image=ubuntu
FROM ${base_image}

ENV WORKING_DIR /app
RUN mkdir -p $WORKING_DIR
WORKDIR $WORKING_DIR

ARG REPO=https://github.com/macdougt/bash-examples.git
ARG REPO_NAME=bash-examples

RUN git clone $REPO

WORKDIR /app/$REPO_NAME

CMD ["bash"]
