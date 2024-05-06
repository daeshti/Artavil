FROM debian:bookworm

RUN apt-get update  -y
RUN apt-get install -y  curl
RUN apt-get install -y  git
RUN apt-get install -y  openssh-server
RUN apt-get install -y  tzdata
RUN apt-get install -y  build-essential
RUN apt-get install -y  gcc
RUN apt-get install -y  g++
RUN apt-get install -y  gdb
RUN apt-get install -y  clang
RUN apt-get install -y  make
RUN apt-get install -y  ninja-build
RUN apt-get install -y  cmake
RUN apt-get install -y  autoconf
RUN apt-get install -y  automake
RUN apt-get install -y  libtool
RUN apt-get install -y  valgrind
RUN apt-get install -y  locales-all
RUN apt-get install -y  dos2unix
RUN apt-get install -y  rsync
RUN apt-get install -y  tar
RUN apt-get install -y  libssl-dev
RUN apt-get clean

ARG REINSTALL_CMAKE_VERSION_FROM_SOURCE="yes"

COPY ./reinstall-cmake.sh /tmp/

RUN if [ "${REINSTALL_CMAKE_VERSION_FROM_SOURCE}" != "no" ]; then \
        chmod +x /tmp/reinstall-cmake.sh && /tmp/reinstall-cmake.sh ${REINSTALL_CMAKE_VERSION_FROM_SOURCE}; \
    fi \
    && rm -f /tmp/reinstall-cmake.sh

RUN service ssh start

WORKDIR /work
