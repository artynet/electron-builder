FROM electronuserland/builder:latest

RUN apt-get update && apt-get install -y --no-install-recommends software-properties-common && dpkg --add-architecture i386 && \
  curl -L https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.10/Release.key > winehq.key && apt-key add winehq.key && \
  apt-add-repository 'deb https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.10/ ./' && \
  apt-get update && \
  apt-get -y purge software-properties-common libdbus-glib-1-2 python3-dbus python3-gi python3-pycurl python3-software-properties && \
  apt-get install -y --no-install-recommends winehq-stable && \
  # clean
  apt-get clean && rm -rf /var/lib/apt/lists/* && unlink winehq.key

RUN curl -L https://github.com/electron-userland/electron-builder-binaries/releases/download/wine-4.0.1-mac/wine-4.0.1-mac.7z > /tmp/wine-home.7z && 7z x -t7z /tmp/wine-home.7z -o/root/.wine && unlink /tmp/wine-home.7z

ENV WINEDEBUG -all,err+all
ENV WINEDLLOVERRIDES winemenubuilder.exe=d
