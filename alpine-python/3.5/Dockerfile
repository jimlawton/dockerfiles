FROM alpine:latest

MAINTAINER Jim Lawton https://github.com/jimlawton

# Adds testing package to repositories
# Install needed packages. Notes:
#   * build-base: used so we include the basic development packages (gcc)
#   * python-dev: are used for gevent e.g.
#   * bash: so we can access /bin/bash
RUN echo "@testing http://dl-4.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories \
  && apk add --update \
              musl \
              build-base \
              python3 \
              python3-dev \
              bash \
              git \
  && pip3.5 install --upgrade pip \
  && rm /var/cache/apk/*

# make some useful symlinks that are expected to exist
RUN cd /usr/bin \
  && ln -sf easy_install-3.5 easy_install \
  && ln -sf idle3.5 idle \
  && ln -sf pydoc3.5 pydoc \
  && ln -sf python3.5 python \
  && ln -sf python-config3.5 python-config \
  && ln -sf pip3.5 pip

# since we will be "always" mounting the volume, we can set this up
CMD python
