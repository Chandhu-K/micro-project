FROM maven:3.9.9-eclipse-temurin-21-jammy as builder
RUN git clone https://github.com/Chandhu-K/micro-project.git
RUN cd micro-project && git checkout containers && mvn install

FROM tomcat:10-jdk21
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=builder /micro-project/target/micro-project-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
LABEL maintainer="Chandhu K"
LABEL version="1.0"
LABEL description="Dockerfile for deploying micro-project on Tomcat"
