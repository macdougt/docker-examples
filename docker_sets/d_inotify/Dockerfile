FROM debian:jessie

RUN apt-get update && apt-get install -y \
	inotify-tools \
	libnotify-bin \
	&& rm -rf /var/lib/apt/lists/*

CMD ["inotifywait","-r","-m","/root"]


