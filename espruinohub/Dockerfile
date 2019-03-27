ARG BUILD_FROM=hassioaddons/base:2.3.2
FROM ${BUILD_FROM}

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN \
    apk add --no-cache \
        nodejs=8.14.0-r0 \
        npm=8.14.0-r0 \
        git=2.18.1-r0 \
        python=2.7.15-r1 \
        build-base=0.5-r1 \
        bluez=5.49-r2 \
        linux-headers=4.4.6-r2 \
        eudev-dev=3.2.5-r2

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