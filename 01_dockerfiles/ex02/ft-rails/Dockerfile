FROM ruby
MAINTAINER kroselin

RUN apt-get update -y && apt-get install -y build-essential libpq-dev nodejs sqlite3

ONBUILD COPY blog/ blog/
ONBUILD WORKDIR blog/

ONBUILD EXPOSE 3000

ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed
