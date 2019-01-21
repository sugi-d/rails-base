FROM ruby:2.6.0-alpine3.8

RUN apk update
RUN apk add --no-cache bash nodejs postgresql tzdata less

RUN cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
ENV TZ Asia/Tokyo

RUN mkdir -p /app
WORKDIR /app

COPY Gemfile Gemfile.lock /app/

ARG RAILS_MASTER_KEY
ENV RAILS_MASTER_KEY ${RAILS_MASTER_KEY:-}

RUN gem install bundler
RUN apk add --no-cache alpine-sdk \
      --virtual .build_deps libxml2-dev libxslt-dev zlib zlib-dev postgresql-dev readline-dev xz-libs libc6-compat
RUN bundle install -j4 --path /usr/local/bundle
# RUN apk del alpine-sdk .build_deps \
#     && rm -rf /tmp/* /var/cache/apk/*

COPY . /app

CMD ["bash"]
