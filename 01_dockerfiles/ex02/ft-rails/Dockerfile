# docker build -t ft-rails:on-build ./01_dockerfiles/ex02/ft-rails/
# --without production
FROM ruby

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y build-essential libpq-dev nodejs sqlite3

ONBUILD COPY app /opt/app

ONBUILD WORKDIR /opt/app/

ONBUILD EXPOSE 3000

ONBUILD RUN bundle install

ONBUILD RUN bundle exec rake db:migrate

ONBUILD RUN bundle exec rake db:seed

LABEL Cornelis Terblanche <m4dm0nk3y.za@gmail.com>