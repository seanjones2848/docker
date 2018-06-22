# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile.old                                     :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: sjones <sjones@student.42.us.org>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2017/08/22 14:11:40 by sjones            #+#    #+#              #
#    Updated: 2017/11/13 14:40:00 by sjones           ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM debian:latest

RUN apt-get update -y \
	&& apt-get upgrade -y

RUN apt-get install -y \
	git wget gcc

WORKDIR $HOME/local
RUN wget https://storage.googleapis.com/golang/go1.8.linux-amd64.tar.gz \
	&& tar -xzvf go1.8.linux-amd64.tar.gz

ENV GOROOT=$HOME/local/go
ENV GOPATH=$HOME/gogs
ENV PATH=$PATH:$GOROOT/bin:$GOPATH/bin
ENV USER=root

WORKDIR $GOPATH/src/github.com/gogits
RUN git clone --depth=1 -b develop https://github.com/gogits/gogs \
	&& go get -u -tags "sqlite" github.com/gogits/gogs

WORKDIR $GOPATH/src/github.com/gogits/gogs
RUN go build -tags "sqlite"

RUN mkdir $GOPATH/src/github.com/gogits/log \
	/root/gogs-repositories \
	/root/data

EXPOSE 3000
ENTRYPOINT ./gogs web
