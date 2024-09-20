FROM openjdk:11 AS BUILD_IMAGE
LABEL "Project"="MiniApp"
LABEL "Author"="tkthinh"

RUN apt update && apt install -y maven
RUN git clone --branch docker https://github.com/tobbie/vprofile-project.git
RUN cd vprofile-project && mvn clean install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
