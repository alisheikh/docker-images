FROM jboss/wildfly

USER root
RUN yum -y install mysql-connector-java mysql

#USER jboss

# Wildfly modules
ADD deployments/wildfly-8.1.0.Final-module-hibernate-main-4.2.19.Final.zip /
ADD deployments/wildfly-8.1.0.Final-module-mojarra-2.1.29-01.zip /
RUN unzip /wildfly-8.1.0.Final-module-hibernate-main-4.2.19.Final.zip -d /opt/jboss/wildfly
RUN unzip /wildfly-8.1.0.Final-module-mojarra-2.1.29-01.zip -d /opt/jboss/wildfly

ADD deployments/zanata.war /opt/jboss/wildfly/standalone/deployments/
RUN chmod o+rw /opt/jboss/wildfly/standalone/deployments/zanata.war

ADD conf/standalone.xml /opt/jboss/wildfly/standalone/configuration/
RUN ln -sf /usr/share/java/mysql-connector-java.jar /opt/jboss/wildfly/standalone/deployments/mysql-connector-java.jar

USER jboss
