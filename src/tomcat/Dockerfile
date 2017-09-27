FROM tomcat:9
MAINTAINER Mathias Kühn kuehn@synerva.de

# Install wget and install/updates certificates
RUN apt-get update \
 && apt-get install -y -q --no-install-recommends \
    ca-certificates \
 && apt-get clean \
 && rm -r /var/lib/apt/lists/*

ENV GPTURL=https://github.com/Esri/geoportal-server-catalog/releases/download/v2.5.0/geoportal-server-2.5.0.zip

ADD $GPTURL /tmp/geoportal.zip

RUN mkdir -p $CATALINA_HOME/webapps/geoportal/WEB-INF/classes/config/

WORKDIR $CATALINA_HOME/webapps/
RUN unzip /tmp/geoportal.zip *.war
RUN rm /tmp/geoportal.zip

# COPY /1.0-SNAPSHOT/my-app-1.0-SNAPSHOT.war /usr/local/tomcat/webapps/myapp/