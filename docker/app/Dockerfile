FROM ruby:2.6.4-alpine
WORKDIR /usr/src/app
RUN apk --no-cache add build-base postgresql-dev
COPY Gemfile Gemfile.lock ./
RUN gem update --system \
    && gem install bundler -v 2.0.2 \
    && bundle install
COPY . .
