# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: sjones <sjones@student.42.us.org>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2017/08/22 14:11:40 by sjones            #+#    #+#              #
#    Updated: 2017/11/28 15:00:47 by sjones           ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM ruby:latest

RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install nodejs -y
RUN gem install rails

ONBUILD COPY . /opt/app

ONBUILD WORKDIR /opt/app

ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed
