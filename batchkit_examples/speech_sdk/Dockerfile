# Copyright (c) Microsoft Corporation.
# Licensed under the MIT License.

# Notes:
#  - Build with working directory set to the repo root.
#  - libgstreamer and plugins need to be installed explicitly here as they are not available as simple pypi packages.

FROM ubuntu:18.04
RUN apt-get update -y && \
    apt-get upgrade -y && \
    apt-get install -y --no-install-recommends \
        pkg-config \
        python3 python3-pip python3-dev \
        build-essential libglib2.0-dev libcairo2-dev libgirepository1.0-dev libssl1.0.0 libasound2 \
        libgstreamer1.0-0 gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly python3-gst-1.0
ARG BATCHKIT_EXAMPLES_PKG
COPY dist/${BATCHKIT_EXAMPLES_PKG}-* /
RUN ln -s /usr/bin/pip3 /usr/bin/pip && \
    ln -s /usr/bin/python3 /usr/bin/python && \
    pip install setuptools wheel && \
    pip install ${BATCHKIT_EXAMPLES_PKG}-*.whl

ENTRYPOINT ["run-batch-client"]
