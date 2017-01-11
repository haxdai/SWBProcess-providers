FROM ubuntu:16.04
MAINTAINER Hasdai Pacheco<me@hasdaipacheco.com>
#Set common variables
ENV TOMCAT_DOWNLOAD_URL http://www-us.apache.org/dist/tomcat/tomcat-9/v9.0.0.M15/bin/apache-tomcat-9.0.0.M15.tar.gz
ENV SWBPROCESS_DOWNLOAD_URL http://www.semanticwebbuilder.org.mx/es_mx/swb/SWB_Process/_rid/1349/_mto/3/_act/download/doc/swbp.war
#Update sources and install basic packages
RUN apt-get update
RUN apt-get install -y unzip
RUN apt-get install -y software-properties-common
#Install Oracle JDK 8
RUN add-apt-repository ppa:webupd8team/java
RUN apt-get update
RUN echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | debconf-set-selections
RUN apt-get install -y oracle-java8-installer
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle
#Download and install apache tomcat
RUN wget --quiet --no-cookies ${TOMCAT_DOWNLOAD_URL} -O /tmp/apache-tomcat.tar.gz
RUN tar xzvf /tmp/apache-tomcat.tar.gz -C /opt
RUN rm /tmp/apache-tomcat.tar.gz
RUN rm -rf /opt/apache-tomcat-9.0.0.M15/webapps/ROOT
RUN rm -rf /opt/apache-tomcat-9.0.0.M15/webapps/docs
RUN rm -rf /opt/apache-tomcat-9.0.0.M15/webapps/examples
RUN rm -rf /opt/apache-tomcat-9.0.0.M15/webapps/host-manager
RUN rm -rf /opt/apache-tomcat-9.0.0.M15/webapps/manager
#Download and explode SWBProcess
RUN wget --quiet --no-cookies ${SWBPROCESS_DOWNLOAD_URL} -O /opt/apache-tomcat-9.0.0.M15/webapps/ROOT.war
RUN unzip /opt/apache-tomcat-9.0.0.M15/webapps/ROOT.war -d /opt/apache-tomcat-9.0.0.M15/webapps/ROOT
RUN rm /opt/apache-tomcat-9.0.0.M15/webapps/ROOT.war
ENV CATALINA_HOME /opt/apache-tomcat-9.0.0.M15/
ENV PATH $PATH:$CATALINA_HOME/bin
EXPOSE 8080
EXPOSE 8009
#Set entry point to start apache tomcat
ENTRYPOINT ["/opt/apache-tomcat-9.0.0.M15/bin/catalina.sh", "run"]
