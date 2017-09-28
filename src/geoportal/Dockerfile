FROM tomcat:9
MAINTAINER Mathias Kühn kuehn@synerva.de

# We are pulling 2.5.0 version of geoportal and harvester
ENV GEOPORTAL_URL=https://github.com/Esri/geoportal-server-catalog/releases/download/v2.5.0/geoportal-server-2.5.0.zip
ENV HARVESTER_URL=https://github.com/Esri/geoportal-server-harvester/releases/download/v2.5.0/geoportal-server-harvester-2.5.0.zip

# Install wget and install/updates certificates
RUN apt-get update \
 && apt-get install -y -q --no-install-recommends \
    ca-certificates \
 && apt-get clean \
 && rm -r /var/lib/apt/lists/*

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64

# Install geoportal web application
ADD $GEOPORTAL_URL /tmp/geoportal.zip

WORKDIR $CATALINA_HOME/webapps/
RUN unzip /tmp/geoportal.zip *.war
RUN rm /tmp/geoportal.zip

COPY tomcat-users.xml $CATALINA_HOME/conf

# Install harvester web application
ADD $HARVESTER_URL /tmp/harvester.zip

WORKDIR $CATALINA_HOME/webapps/
RUN unzip /tmp/harvester.zip *.war
RUN rm /tmp/harvester.zip

