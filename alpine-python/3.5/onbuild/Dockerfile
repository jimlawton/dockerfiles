FROM jlawton/alpine-python:3.5

MAINTAINER Jim Lawton https://github.com/jimlawton

# install requirements
# this way when you build you won't need to install again
# ans since COPY is cached we don't need to wait
ONBUILD COPY ./requirements.txt /tmp/requirements.txt
ONBUILD RUN pip install -r /tmp/requirements.txt

