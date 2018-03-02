FROM ruby:2.3.4

RUN apt-get update && \
	apt-get install -y nodejs && \
	gem install rails -v 4.2.7 && \
	gem install json && \
	mkdir -p /opt/app


ONBUILD WORKDIR /opt/app
ONBUILD ADD . /opt/app

ONBUILD EXPOSE 3000
ONBUILD RUN bundle update && \
			bundle install && \
			rake db:migrate && \
			rake db:seed 


#docker build -t ex02 .
#docker build -t cheat .
#docker run -d -p 3000:3000 cheat