FROM ubuntu:latest


EXPOSE 3000

# Update the repository sources list
RUN apt-get update && apt-get install -y \
	    mlocate \
	    build-essential \
	    npm \
	    git \
	    git-core \
	    openssl \
	    libssl-dev \ 
	    curl \
	    expect

#RUN npm install -g npm
#RUN npm cache clean -f
RUN npm install -g n
RUN n stable
RUN npm install -g grunt-cli
RUN npm install -g bower
RUN npm install -g yo

# Add the .bashrc
ADD .bashrc ~/.bashrc

RUN adduser --disabled-password --gecos "" yeoman
RUN echo "yeoman ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Run as yeoman
USER yeoman
RUN mkdir /tmp/test1
WORKDIR "/tmp/test1"
RUN /bin/sh -c 'cd /tmp/test1;npm install generator-express'

USER root
COPY yoExpress.exp /tmp/test1/
RUN chown yeoman yoExpress.exp
RUN chmod 777 yoExpress.exp

USER yeoman
RUN /bin/sh -c 'expect yoExpress.exp'

# Clean up the directory
RUN rm -rf node_modules
RUN npm cache clean
RUN npm install

CMD ["grunt"]

# docker build -t yo_express_image 
# docker run -d --name="yo_express_container" -p 3000:3000 yo_express_image
# curl http://localhost:3000





