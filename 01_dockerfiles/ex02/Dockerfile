FROM ruby:latest

RUN mkdir -p /opt/app
WORKDIR /opt/app

RUN apt-get update && \
    apt-get install -y nodejs && \
    apt-get install -y sqlite3 && \
    gem install rails && \
    rm -rf /var/lib/apt/lists/*

COPY . /opt/app

EXPOSE 3000

ONBUILD RUN bundle install && \
            rake db:migrate && \
            rake db:seed 