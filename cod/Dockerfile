FROM ubuntu
LABEL maintainer "Mateusz Wojcik"

RUN apt-get update
RUN dpkg --add-architecture i386
RUN apt-get update
RUN apt-get install -y iproute2 mailutils postfix curl wget file tar bzip2 gzip unzip bsdmainutils python util-linux ca-certificates binutils bc jq tmux lib32gcc1 libstdc++6 libstdc++6:i386 libstdc++5:i386
RUN apt-get install -y aria2

RUN useradd -ms /bin/bash coduoserver
USER coduoserver

WORKDIR /home/coduoserver
RUN wget -O linuxgsm.sh https://linuxgsm.sh 
RUN chmod +x linuxgsm.sh
RUN bash linuxgsm.sh coduoserver
RUN mkdir /home/coduoserver/lgsm/tmp
WORKDIR /home/coduoserver/lgsm/tmp
COPY coduo-lnxded-1.51b-full.tar.bz2 coduo-lnxded-1.51b-full.tar.bz2
WORKDIR /home/coduoserver/
RUN ./coduoserver auto-install

CMD ./coduoserver start