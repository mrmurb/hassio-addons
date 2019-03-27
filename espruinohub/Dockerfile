ARG BUILD_FROM=hassioaddons/base:3.0.1
FROM ${BUILD_FROM}

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN \
    set -o pipefail \
    && apk add --no-cache \
        git=2.20.1-r0 \
        python2=2.7.15-r3 \
        build-base=0.5-r1 \
        bluez=5.50-r0 \
        linux-headers=4.18.13-r1 \
        eudev-dev=3.2.7-r0

RUN \
    set -o pipefail \
    && echo '@3.8 http://dl-cdn.alpinelinux.org/alpine/v3.8/main' >> /etc/apk/repositories \
    && apk add --no-cache \
        nodejs@3.8=8.14.0-r0 \
        npm@3.8=8.14.0-r0

WORKDIR /opt
RUN git clone https://github.com/espruino/EspruinoHub espruinohub

WORKDIR /opt/espruinohub
RUN npm i --unsafe-perm

COPY rootfs /

ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

LABEL \
    io.hass.name="EspruinoHub" \
    io.hass.description="An BLE to MQTT thing" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version="${BUILD_VERSION}"

#RUN git clone https://github.com/espruino/EspruinoHub /var/espruinohub

#WORKDIR /var/espruinohub

#RUN npm install --unsafe-perm

#COPY run.sh /var/espruinohub/run.sh
#RUN chmod +x /var/espruinohub/run.sh

#CMD /var/espruinohub/run.sh