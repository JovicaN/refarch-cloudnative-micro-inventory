FROM openjdk:8-alpine
VOLUME /tmp

# Install prereqs
RUN apk --no-cache update \
 && apk add jq bc wget bash

COPY agents/ /agents/

# Add the new relic agent
RUN wget https://download.newrelic.com/newrelic/java-agent/newrelic-agent/current/newrelic-java.zip -O /tmp/newrelic.zip \
  && unzip -d /agents /tmp/newrelic.zip newrelic/newrelic.jar \
  && rm /tmp/newrelic.zip

ADD app.jar app.jar

# Copy agent files
COPY startup.sh startup.sh

EXPOSE 8080
ENTRYPOINT ["./startup.sh"]
