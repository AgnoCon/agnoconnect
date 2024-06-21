    AgnoConnect Installation 
<------------------------------>

1. apt-get update && apt-get install -yq gnupg2 wget lsb-release

2. sudo apt-get update && sudo apt-get install -y git-core build-essential python-is-python3 python3-dev autoconf automake libtool libncurses5 libncurses5-dev make libjpeg-dev pkg-config zlib1g-dev sqlite3 libsqlite3-dev libpcre3-dev libspeexdsp-dev libspeex-dev libedit-dev libldns-dev liblua5.1-0-dev libcurl4-gnutls-dev libapr1-dev yasm libsndfile-dev libopus-dev libtiff-dev libavformat-dev libswscale-dev libswresample-dev libpq-dev zip

3.  cd /usr/src/

4.  git clone https://github.com/AgnoCon/agnoconnect.git

5.  chmod 777 -R agnoconnect
   
6.  cd agnoconnect
  
7.  git config pull.rebase true

8.  ./bootstrap.sh -j

9. ./configure --enable-core-pgsql-support

10. make

11. make install

12. make all cd-sounds-install cd-moh-install

13 ln -s /usr/local/agnoconnect/bin/freeswitch /usr/bin/agnoconnect

14 ln -s /usr/local/agnoconnect/bin/fs_cli /usr/bin/fs_cli

15 cd /usr/local

16 sudo groupadd agnoconnect

17 sudo adduser --quiet --system --home /usr/local/agnoconnect --gecos "agnoconnect open source softswitch" --ingroup agnoconnect agnoconnect --disabled-password

18 chown -R agnoconnect:agnoconnect /usr/local/agnoconnect/

19 chmod -R ug=rwX,o=rwX /usr/local/agnoconnect/

20 chmod -R u=rwx,g=rwx,o=rwX /usr/local/agnoconnect/bin/*

21 cp /usr/src/agnoconnect/debian/agnoconnect-systemd.agnoconnect.service /etc/systemd/system/agnoconnect.service

22 systemctl daemon-reload

23 systemctl enable agnoconnect

26 systemctl start agnoconnect
