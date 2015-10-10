FROM ubuntu:latest

# Update the repository sources list
RUN apt-get update && apt-get install -y \
	    mlocate \
	    git \
	    git-core \
	    openssl \
	    libssl-dev \ 
	    curl \
	    expect \
	    tree \
	    wget \
	    python

RUN wget https://raw.githubusercontent.com/macdougt/bash-examples/master/install_t.bash
RUN bash ./install_t.bash

