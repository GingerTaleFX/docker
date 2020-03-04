FROM ruby:2.6.1
MAINTAINER kroselin

RUN apt-get update -y && apt-get install -y build-essential libpq-dev nodejs sqlite3 git
RUN gem update && gem install rails
RUN gem install bundler:1.3.0
RUN gem install rake -v 13.0.1
# Installing yarn
#RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
#RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
# RUN apt-get update && apt-get install yarn
ONBUILD COPY blog/ blog/
ONBUILD WORKDIR blog/

ONBUILD EXPOSE 3000

ONBUILD RUN bundle install
ONBUILD RUN rake db:migrate
# ONBUILD RUN rake _13.0.1_ db:seed
