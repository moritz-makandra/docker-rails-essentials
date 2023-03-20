ARG RUBY_VERSION=2.6.9

FROM ruby:${RUBY_VERSION}

WORKDIR /

RUN gem update --system

RUN gem install bundler

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor > /etc/apt/trusted.gpg.d/yarn.gpg\
	&&	echo "deb https://dl.yarnpkg.com/debian/ stable main" > /etc/apt/sources.list.d/yarn.list

ARG DEBIAN_PACKAGES
RUN apt-get update \
	&&  DEBIAN_FRONTEND=noninteractive apt-get -y install --no-install-recommends \
	nodejs yarn \
        && rm -rf /var/cache/apt \
	&& rm -rf /var/lib/apt/lists/*

RUN yarn global add webpack webpack-cli@4.0.0


LABEL ruby_version=$RUBY_VERSION
