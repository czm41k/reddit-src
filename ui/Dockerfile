FROM debian:stretch
RUN apt-get update \
    && apt-get install -y ruby-full ruby-dev build-essential dnsutils \
    && gem install bundler --no-ri --no-rdoc

ENV APP_HOME /app
RUN mkdir $APP_HOME

WORKDIR $APP_HOME
ADD ./src/ui/Gemfile* $APP_HOME/
RUN bundle install
ADD ./src/ui $APP_HOME/
# RUN mkdir ${APP_HOME}/views
# ADD ./src/ui/views/* ${APP_HOME}/views/

ENV POST_SERVICE_HOST post
ENV POST_SERVICE_PORT 5000
ENV COMMENT_SERVICE_HOST comment
ENV COMMENT_SERVICE_PORT 9292

CMD ["puma"]