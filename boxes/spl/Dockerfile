FROM esolang/build-base

ENV BUILD_PACKAGES="" \
    RUNTIME_PACKAGES="python3 libbsd-dev"

RUN apk add --update $BUILD_PACKAGES $RUNTIME_PACKAGES && \
    git clone --depth 1 https://github.com/db314159/Spl.git ~/Spl && \
    sed -i 's/or trimmed == "openyourmind"/or trimmed == "openthymind"/' ~/Spl/splc.py && \
    rm -rf /var/cache/apk/* /tmp/*

COPY script /bin/script

RUN ln -s /bin/script /bin/spl && \
    chmod 744 /bin -R

WORKDIR /root

CMD [ "script" ]
