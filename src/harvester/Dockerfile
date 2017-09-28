FROM tomcat:9
MAINTAINER Mathias Kühn kuehn@synerva.de

# Install wget, java, and install/updates certificates
RUN apt-get update \
 && apt-get install -y -q --no-install-recommends \
    ca-certificates git maven \
    openjdk-8-jdk="$JAVA_DEBIAN_VERSION" \
    ca-certificates-java="$CA_CERTIFICATES_JAVA_VERSION" \
 && apt-get clean \
 && rm -r /var/lib/apt/lists/*

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64

ENV GITURL=https://github.com/Esri/geoportal-server-harvester.git

WORKDIR /tmp
RUN git clone ${GITURL} harvester
WORKDIR /tmp/harvester
RUN mvn package -DskipTests

WORKDIR $CATALINA_HOME/webapps/

RUN cp /tmp/harvester/geoportal-application/geoportal-harvester-war/target/*.war harvester.war
