# The image is big TODO make way smaller
# how do I package the install without the installer
# sample command: docker run -v `pwd`:`pwd` -w `pwd` -t -i ffm_t -i input_file.mp4 -vn -ar 44100 -ac 2 -ab 192k -f mp3 output_file.mp3
# instructions: https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu
# Dockerfile
FROM ubuntu

RUN apt-get update
RUN apt-get -y --force-yes install autoconf automake build-essential libass-dev libfreetype6-dev \
  libsdl1.2-dev libtheora-dev libtool libva-dev libvdpau-dev libvorbis-dev libxcb1-dev libxcb-shm0-dev \
  libxcb-xfixes0-dev pkg-config texinfo zlib1g-dev

RUN mkdir /ffmpeg_sources

RUN apt-get -y install  wget
RUN apt-get -y install yasm
#RUN apt-get -y install libx264-dev
RUN apt-get -y install libmp3lame-dev

WORKDIR /ffmpeg_sources
RUN wget http://ffmpeg.org/releases/ffmpeg-snapshot.tar.bz2
RUN tar xjvf ffmpeg-snapshot.tar.bz2
WORKDIR /ffmpeg_sources/ffmpeg
ENV PATH "$HOME/bin:$PATH"
ENV PKG_CONFIG_PATH "/ffmpeg_sources/ffmpeg_build/lib/pkgconfig"

RUN ./configure \
  --prefix="$HOME/ffmpeg_build" \
  --pkg-config-flags="--static" \
  --extra-cflags="-I/ffmpeg_sources/ffmpeg_build/include" \
  --extra-ldflags="-L/ffmpeg_sources/ffmpeg_build/lib" \
  --bindir="/ffmpeg_sources/bin" \
#  --enable-gpl \
  --enable-libass \
#  --enable-libfdk-aac \
  --enable-libfreetype \
  --enable-libmp3lame
#  --enable-libopus \
#  --enable-libtheora \
#  --enable-libvorbis \
#  --enable-libvpx \
#  --enable-libx264 \
#  --enable-libx265 \
#  --enable-nonfree
RUN make
RUN make install
RUN make distclean
RUN hash -r

CMD           ["--help"]
ENTRYPOINT    ["/ffmpeg_sources/bin/ffmpeg"]

