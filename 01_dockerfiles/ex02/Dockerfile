FROM ruby

WORKDIR /parentopt/app
RUN apt-get update -y && apt-get upgrade -y &&\
    apt-get install -y build-essential libpq-dev nodejs && \
	gem install rails

ONBUILD EXPOSE 3000
ONBUILD RUN	rails new server && cd server
ONBUILD WORKDIR /parentopt/app/server
ONBUILD RUN bundle install && \ 
	rake db:migrate && \
	rake db:seed
