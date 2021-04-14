FROM linux-agent-i386:v1

LABEL author=eduardo.fernandez author_email=eduardo.fernandez@smartmatic.com

RUN sudo apt update                                                                                                             && \
    sudo apt install -y --no-install-recommends fonts-freefont-ttf gettext google-mock libao-dev libarchive-dev                    \
                                                libasound2-dev libcups2-dev libcurl-openssl1.0-dev libevdev-dev                    \
                                                libgtest-dev libgpiod-dev libgtkmm-3.0-dev libi2c-dev libjavascriptcoregtk-3.0-dev \
                                                libnutclient-dev libow-dev libpcre3-dev libpcsclite-dev libpng-dev                 \
                                                libprotobuf-dev libqrencode-dev libsane-dev libsoundtouch-dev libudev-dev          \
                                                libusb-1.0-0-dev libvorbis-dev libwebkit2gtk-4.0-dev libxerces-c-dev               \
                                                libxext-dev libxml-security-c-dev libxml2-dev libxslt1-dev libzbar-dev             \
                                                libssl1.0-dev protobuf-compiler uuid-dev unzip

RUN sudo apt remove libcurl4                   && \
    sudo apt install -y libcurl3               && \
    sudo apt install -y libcurl-openssl1.0-dev

RUN wget https://github.com/google/googletest/archive/master.zip && \
    unzip master.zip -d .                                        && \
    cd googletest-master                                         && \
    cmake .                                                      && \
    sudo make install
