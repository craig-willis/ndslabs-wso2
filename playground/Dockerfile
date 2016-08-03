#ndslabs/wso2is-playground
FROM centos:7

RUN yum update -y && \
    yum install -y curl java-1.7.0-openjdk java-1.7.0-openjdk-devel maven svn wget \
    cd / && svn co http://svn.wso2.org/repos/wso2/carbon/platform/branches/turing/products/is/5.0.0/modules/samples/oauth2/playground2/ && \
    curl http://apache.cs.utah.edu/tomcat/tomcat-8/v8.5.4/bin/apache-tomcat-8.5.4.tar.gz -O && \
    tar xvfz apache-tomcat-8.5.4.tar.gz 

COPY pom.xml /playground2/pom.xml
RUN cd playground2/ && mvn package && \
    cp target/playground2.war /apache-tomcat-8.5.4/webapps/


EXPOSE 8080
CMD ["/apache-tomcat-8.5.4/bin/catalina.sh", "run"]
