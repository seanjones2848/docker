# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: sjones <sjones@student.42.us.org>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2017/08/21 13:42:46 by sjones            #+#    #+#              #
#    Updated: 2017/08/21 14:56:45 by sjones           ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM alpine

MAINTAINER Sean jones <sjones@student.42.us.org>

RUN apk update && apk upgrade

RUN apk add --no-cache build-base\
	lua5.2-libs\
	musl\
	vim

CMD vim
