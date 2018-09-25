FROM debian

RUN apt-get update && apt-get upgrade -y
RUN apt-get install wget -y\
	&& apt-get install lbzip2 -y
RUN adduser --disabled-login teamspeak
RUN cd /home/teamspeak
RUN wget http://dl.4players.de/ts/releases/3.1.2/teamspeak3-server_linux_amd64-3.1.2.tar.bz2
RUN tar xvf teamspeak3-server_linux_amd64-3.1.2.tar.bz2
RUN cd teamspeak3-server_linux_amd64 && mv * /home/teamspeak && cd .. && rm -rf teamspeak3-server_linux_amd64-3.1.2.tar.bz2
RUN touch /home/teamspeak/.ts3server_license_accepted

WORKDIR /home/teamspeak

EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011
EXPOSE 41144

COPY ts3.ini /home/teamspeak/ts3.ini
USER teamspeak

ENTRYPOINT ["sh","ts3server_minimal_runscript.sh", "inifile=ts3.ini"]
