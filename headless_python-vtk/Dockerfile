FROM syuki/headless-gpu:415.27

# set timezone
RUN apt-get update && apt-get install -y tzdata locales && locale-gen en_US.UTF-8 && ln -fs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && dpkg-reconfigure -f noninteractive tzdata

# python
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \
          wget ca-certificates openssl \
    python3-dev \
    python3-wheel \
    python3-setuptools && \
    wget https://bootstrap.pypa.io/get-pip.py && python3 get-pip.py && \
    rm -rf /var/lib/apt/lists/*

# vtk
RUN pip3 install vtk

RUN mkdir -p /work /data

WORKDIR /work

ENTRYPOINT ["/bin/bash"]
