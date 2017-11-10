FROM dataspeedinc/mplabx

#ADD microchip /opt/microchip

RUN dpkg --add-architecture i386 \
    && apt-get update -yq \
    && apt-get install -yq --no-install-recommends \
	texlive-latex-base texlive-latex-extra texlive-fonts-recommended \
        make lmodern

