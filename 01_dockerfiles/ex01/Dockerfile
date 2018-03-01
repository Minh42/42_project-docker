# Base system
From debian:latest

# Set the Teamspeak version to download
ENV TSV=3.0.13.8
ENV TS_DIRECTORY=/opt/teamspeak

# Download and install Teamspeak
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y bzip2 && \
    apt-get install -y w3m && \
    apt-get install -y wget && \
    wget http://dl.4players.de/ts/releases/${TSV}/teamspeak3-server_linux_amd64-${TSV}.tar.bz2 -O /tmp/teamspeak.tar.bz2 && \
    tar jxf /tmp/teamspeak.tar.bz2 -C /opt && \
    mv /opt/teamspeak3-server_* ${TS_DIRECTORY} && \
    rm /tmp/teamspeak.tar.bz2 && \
    apt-get purge -y bzip2 w3m wget && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/*

# Create group and users
RUN groupadd -g 503 teamspeak &&\
  useradd -u 503 -g 503 -d ${TS_DIRECTORY} teamspeak &&\
  mkdir /data &&\
  chown -R teamspeak:teamspeak ${TS_DIRECTORY} /data

# Open ports for TS3
EXPOSE 9987/UDP 30033/TCP 10011/TCP 41144/TCP
USER   teamspeak
WORKDIR $TS_DIRECTORY

# Run shell script to get root's id and token
ENTRYPOINT ["./ts3server_minimal_runscript.sh", "createinifile=1"]