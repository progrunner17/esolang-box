FROM esolang/build-base

RUN cd /tmp && \
    curl -m $TIMEOUT https://github.com/graue/esofiles/raw/master/beatnik/impl/BEATNIK.c -L -o /tmp/BEATNIK.c && \
    gcc -Wall -O2 /tmp/BEATNIK.c -o /usr/bin/BEATNIK && \
    rm -rf /var/cache/apk/* /tmp/*

COPY script /bin/script

RUN ln -s /bin/script /bin/beatnik && \
    chmod 744 /bin -R

WORKDIR /root

CMD [ "script" ]
