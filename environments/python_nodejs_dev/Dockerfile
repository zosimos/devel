FROM zosimos/nodejs_dev:latest

ENV LD_LIBRARY_PATH=/usr/local/lib:$HOME/local/lib \
    LD_RUN_PATH=$LD_LIBRARY_PATH

RUN yum -y update \
    && yum install yum-utils -y; yum clean all \
    && yum-builddep python -y; yum clean all \
    && yum -y groupinstall "Development Tools" \
    && yum install gcc gcc-c++ -y; yum clean all \
    && yum install libffi-devel libxml2-devel libxslt-devel -y; yum clean all \
    && yum install openssl-devel -y; yum clean all \
    && yum install deltarpm -y; yum clean all \
    && yum install which cd screen wget tar gzip -y; yum clean all \
    && rm -rf /tmp/src \
    && echo "------------------------- Install Python 3.7.0 --------------------------" \
    && mkdir /tmp/src \
    && cd /tmp/src \
    && curl -O https://www.python.org/ftp/python/3.7.0/Python-3.7.0.tgz \
    && tar xzvf Python-* \
    && cd Python-3.7.0 \
    && ./configure --enable-optimizations --enable-shared --with-system-expat --with-system-ffi \
    && make \
    && make install \
    && cd / \
    && rm -rf /tmp/src \
    && /usr/local/bin/pip3.7 install --upgrade pip setuptools \
    && /usr/local/bin/pip3.7 install requests -U \
    && /usr/local/bin/python3.7 -c "print('Python has been installed successfully')"


CMD ['/bin/bash']
