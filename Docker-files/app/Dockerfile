FROM openjdk:11 as stage1
RUN apt update && apt install maven -y
RUN git clone https://github.com/shwetank142/vprofile-project.git 
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11 
LABEL "Project"="Vprofile"
LABEL "author"="Shwetank"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=stage1 vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh","run"]
