# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: sjones <sjones@student.42.us.org>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2017/08/21 16:59:54 by sjones            #+#    #+#              #
#    Updated: 2017/08/21 18:01:46 by sjones           ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM debian:latest

MAINTAINER sjones

ENV DEBIAN_FRONTEND=noninteractive TERM=linux TZ='America/Los_Angeles'
RUN echo "$TZ" > /etc/timezone && dpkg-reconfigure tzdata

RUN apt-get update &&\
	apt-get install -y bzip2 curl wget

WORKDIR /tmp

RUN TEAMSPEAK_LINK=$( \
	curl https://www.teamspeak.com/en/downloads | \
	grep -oE 'http://dl.4players.*server_linux_amd64.*tar.bz2' | \
	sed -n 2p) \
	&& FILE=$(basename $TEAMSPEAK_LINK) \
	&& mkdir /teamspeak \
	&& wget $TEAMSPEAK_LINK \
	&& bzip2 -d /tmp/$FILE \
	&& FILETAR=${FILE%.*} \
	&& mkdir /tmp/teamspeak \
	&& tar -xf $FILETAR -C /tmp/teamspeak \
	&& cd /tmp/teamspeak/teamspeak3-server_linux_amd64 \
	&& cp -r * /teamspeak \
	&& rm -r /tmp/*

VOLUME /teamspeak/files /teamspeak/logs /teamspeak/configsp
EXPOSE 9987/udp 10011 30033

WORKDIR /teamspeak
ENTRYPOINT ./ts3server_minimal_runscript.sh
