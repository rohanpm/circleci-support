# This image aims to be equivalent to the upstream circleci/python images
# except that the installed Python is replaced with Python 2.6.x.

FROM circleci/python:2.7.15-jessie
LABEL source=https://github.com/rohanpm/circleci-support

USER root

ADD deadsnakes.gpgkey /tmp/deadsnakes.gpgkey

RUN \
  GET_PIP_URL=https://github.com/pypa/get-pip/raw/3de61057f0037f4a12b4a3c6936e9ee91d07a811/2.6/get-pip.py && \
  GET_PIP_SUM=02b9553a4fc36740ff183c40ce413d4ae840d17099e16a43ef4f7996230ea173 && \
  set -ex && \
  echo "deb http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu trusty main" \
    > /etc/apt/sources.list.d/deadsnakes.list && \
  apt-key add /tmp/deadsnakes.gpgkey && \
  rm -f /tmp/deadsnakes.gpgkey && \
  apt-get update && \
  apt-get remove python2.7 && \
  apt-get autoremove && \
  rm -rf /usr/local/bin/python* && \
  apt-get install python2.6 python2.6-dev && \
  curl -L $GET_PIP_URL -o /tmp/get-pip.py && \
  echo "$GET_PIP_SUM  /tmp/get-pip.py" | sha256sum --check && \
  python2.6 /tmp/get-pip.py -v && \
  rm -f /tmp/get-pip.py && \
  pip install pipenv && \
  ln -s /usr/bin/python2.6 /usr/bin/python

USER circleci
