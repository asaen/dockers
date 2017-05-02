FROM ubuntu:16.04

RUN apt-get update
RUN apt-get install -y wget curl locales perl libfontconfig
RUN rm -rf /var/lib/apt/lists/*

# UTF-8 locale
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LC_ALL en_US.UTF-8

# download and install texlive
RUN wget -nv -O install-tl.tar.gz http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
RUN mkdir -p install-tl
RUN tar -xzf install-tl.tar.gz -C install-tl --strip-components=1
ADD texlive.profile .
RUN ./install-tl/install-tl --persistent-downloads --profile=texlive.profile
RUN rm install-tl.tar.gz && rm -r install-tl
ENV PATH /usr/local/texlive/bin/x86_64-linux:$PATH
