FROM ubuntu:latest

ARG timezone=EST5EDT

RUN apt-get update && \
        apt-get install -y tzdata && \
	ln -fs /usr/share/zoneinfo/${timezone} /etc/localtime && \
	dpkg-reconfigure --frontend noninteractive tzdata && \
        apt-get install -y \
	    mlocate \
	    git \
	    git-core \
	    openssl \
	    libssl-dev \ 
	    curl \
	    expect \
	    tree \
	    wget \
	    vim \
	    python3; apt-get autoclean; apt-get clean; apt-get autoremove

# Link python to python3
RUN ln -s /usr/bin/python3 /usr/bin/python

RUN wget https://raw.githubusercontent.com/macdougt/bash-examples/master/install_t.bash
RUN yes | bash ./install_t.bash -u root

# source ~/.profile to enable the bash pieces that were added
