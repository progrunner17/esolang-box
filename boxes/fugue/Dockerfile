FROM esolang/ubuntu-base

ENV BUILD_PACKAGES="" \
    RUNTIME_PACKAGES="gcc-multilib"

RUN dpkg --add-architecture i386 && \
    apt-get update && \
    apt-get install $RUNTIME_PACKAGES $BUILD_PACKAGES -y && \
    curl -m $TIMEOUT https://github.com/graue/esofiles/raw/master/fugue/impl/fugue_x86.c -LO && \
    sed -i "s/stricmp/strcasecmp/" fugue_x86.c && \
    gcc -Wall -O2 fugue_x86.c -o fugue && \
    mv fugue ~/fugue && \
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/*

COPY script /bin/script

RUN ln -s /bin/script /bin/fugue && \
    chmod 744 /bin -R

WORKDIR /root

CMD [ "script" ]
