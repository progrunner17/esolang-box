FROM esolang/python2

ENV BUILD_PACKAGES="recode" \
    RUNTIME_PACKAGES=""

RUN apk add $BUILD_PACKAGES $RUNTIME_PACKAGES && \
    curl -m $TIMEOUT "https://esolangs.org/wiki/FerNANDo" -L | awk -F "</?pre>" '{print $44}' RS="b\bb" | recode HTML..u8 | tr -cd '\0-\200' > ~/fernando.py && \
    apk del $BUILD_PACKAGES && \
    rm -rf /var/cache/apk/* /tmp/*

COPY script /bin/script

RUN ln -s /bin/script /bin/fernando && \
    rm /bin/python2 && \
    chmod 744 /bin -R

WORKDIR /root

CMD [ "script" ]
