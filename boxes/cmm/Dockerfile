FROM esolang/build-base

ENV BUILD_PACKAGES="perl" \
    RUNTIME_PACKAGES=""

RUN apk add $BUILD_PACKAGES $RUNTIME_PACKAGES && \
    touch /usr/bin/latex && \
    cd /tmp && \
    curl -m $TIMEOUT https://caml.inria.fr/distrib/ocaml-3.10/ocaml-3.10.2.tar.gz -LO && \
    tar xfz ocaml-3.10.2.tar.gz && \
    cd ocaml-3.10.2 && \
    ./configure && \
    make world && \
    make opt && \
    make install && \
    cd /tmp && \
    curl -m $TIMEOUT ftp://www.eecs.harvard.edu/pub/nr/noweb.tgz -LO && \
    tar xzf noweb.tgz && \
    cd noweb-2.11b/src && \
    make && \
    (find shell -perm /111 -type f | xargs -I {} cp {} /usr/bin) && \
    cd /tmp && \
    curl -m $TIMEOUT https://www.lua.org/ftp/lua-4.0.1.tar.gz -LO && \
    tar xzf lua-4.0.1.tar.gz && \
    cd lua-4.0.1 && \
    make && \
    make install && \
    git clone --depth 1 https://github.com/nrnrnr/qc-- && \
    cd qc--/mk && \
    make && \
    (make install || echo 'Ignoring make install error') && \
    cd .. && \
    ./configure && \
    apk del $BUILD_PACKAGES && \
    rm -rf /var/cache/apk/* /tmp/*

COPY script /bin/script

RUN ln -s /bin/script /bin/rprogn && \
    rm /bin/lua && \
    chmod 744 /bin -R

WORKDIR /root

CMD [ "script" ]
