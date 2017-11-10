FROM ubuntu:xenial

#ADD microchip /opt/microchip

RUN dpkg --add-architecture i386 \
    && apt-get update -yq \
    && apt-get install -yq --no-install-recommends curl libc6:i386 \
    libx11-6:i386 libxext6:i386 libstdc++6:i386 libexpat1:i386 \
    libxext6 libxrender1 libxtst6 libgtk2.0-0 \
    tree

# Download and install XC32 compiler
RUN curl -fSL -A "Mozilla/4.0" -o /tmp/xc32.run "http://www.microchip.com/mplabxc32linux" \
    && chmod a+x /tmp/xc32.run \
    && /tmp/xc32.run --mode unattended --unattendedmodeui none \
        --netservername localhost --LicenseType FreeMode \
    && rm /tmp/xc32.run
ENV PATH /opt/microchip/xc32/`ls /opt/microchip/xc32/ | awk '{print $1}'`/bin:$PATH

# Download and install XC16 compiler
RUN curl -fSL -A "Mozilla/4.0" -o /tmp/xc16.run "http://www.microchip.com/mplabxc16linux" \
    && chmod a+x /tmp/xc16.run \
    && /tmp/xc16.run --mode unattended --unattendedmodeui none \
        --netservername localhost --LicenseType FreeMode \
    && rm /tmp/xc16.run
ENV PATH /opt/microchip/xc16/`ls /opt/microchip/xc16/ | awk '{print $1}'`/bin:$PATH

# Download and install MPLAB X IDE
# Use url: http://www.microchip.com/mplabx-ide-linux-installer to get the latest version
RUN curl -fSL -A "Mozilla/4.0" -o /tmp/mplabx-installer.tar "http://www.microchip.com/mplabx-ide-linux-installer" \
    && tar xf /tmp/mplabx-installer.tar && rm /tmp/mplabx-installer.tar \
    && USER=root ./*-installer.sh --nox11 \
        -- --unattendedmodeui none --mode unattended \
    && rm ./*-installer.sh

# Download and install PIC32 Legacy libraries
RUN curl -fSL -A "Mozilla/4.0" -o /tmp/pic32-legacy-installer.tar "ww1.microchip.com/downloads/en/softwarelibrary/pic32%20peripheral%20library/pic32%20legacy%20peripheral%20libraries%20linux%20(2).tar" \
    && tar xf /tmp/pic32-legacy-installer.tar && rm /tmp/pic32-legacy-installer.tar \
    && ./PIC32\ Legacy\ Peripheral\ Libraries.run -- --unattendedmodeui none --mode unattended --prefix /opt/microchip/xc32/`ls /opt/microchip/xc32/ | awk '{print $1}'`/ \
    && rm ./PIC32\ Legacy\ Peripheral\ Libraries.run
