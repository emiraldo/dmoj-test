FROM ubuntu:18.04

ENV JUDGE_NAME='Emiraldo'
ENV JUDGE_KEY='rj%e8mvyz+9@4)f#-dtwy35awm=t&+4+wha=^o-2)ja1c)ndlo'
ENV JUDGE_SITE='site'

RUN useradd -m -U judge && \
    sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list && \
    sed -i 's/security.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list && \
    apt-get dist-upgrade -y && \
    apt-get -y update && \
    apt-get install -y --no-install-recommends python python3-dev python3 gcc g++ wget file nano vim git ca-certificates python3-pip build-essential libseccomp-dev python3-setuptools && \
    apt-get autoremove -y && apt-get clean

WORKDIR /judge
RUN git clone https://github.com/schoj/judge /judge --depth=1
RUN pip3 install wheel && \
    pip3 install -r requirements.txt -i https://mirrors.ustc.edu.cn/pypi/web/simple
RUN python3 setup.py develop && \
    mkdir /problems && touch /problems/init.yml

ADD startup.sh /

CMD sh /startup.sh
