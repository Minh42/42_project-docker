FROM ruby:2.3.4

RUN apt-get update && apt-get install -y nodejs && gem install rails && mkdir -p /opt/app

ONBUILD COPY . /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD EXPOSE 3000
ONBUILD RUN bundle install && rake db:migrate && rake db:seed

#docker build -t minh42/ruby:latest $PWD
#docker build -t minh42/ruby:2.3.4 /Users/mpham/Documents/docker/01_dockerfiles/ex02
#docker build -f Dockerfile .