FROM ruby:2.6.1
MAINTAINER kroselin

RUN apt-get update -y && apt-get install -y \
		build-essential \
		libpq-dev \
		nodejs \
		sqlite3 \
		gem \
		yarn
RUN apt-get upgrade -y yarn
RUN gem install bundler:1.17.2
RUN gem install rails --no-document
RUN gem install rake -v 13.0.1 --no-document
RUN gem install yarn

# Run on ft-rails:on-build
ONBUILD COPY blog/ /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD EXPOSE 3000
ONBUILD RUN yarn install --check-files
ONBUILD RUN bundle install
ONBUILD RUN rake _13.0.1_ db:migrate
ONBUILD RUN rake _13.0.1_ db:seed
#ONBUILD RUN rake _13.0.1_
