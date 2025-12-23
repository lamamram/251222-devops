FROM tomcat:11-jdk21

RUN useradd -M -d /usr/local/tomcat -U tomcat && \
    chown -R tomcat:tomcat /usr/local/tomcat

COPY --chown=tomcat:tomcat ./target/java-sb.war.original /usr/local/tomcat/webapps/java-sb.war

USER tomcat
WORKDIR /usr/local/tomcat/webapps

HEALTHCHECK \
  --interval=30s \
  --timeout=30s \
  --start-period=5s \
  --retries=3 \
  CMD grep "Server startup" /usr/local/tomcat/logs/catalina.*.log
