FROM mosqoo/tomcat:8.5.5
MAINTAINER mosqoo <mosqoo@qq.com>
# jenkins
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN ["rm", "-fr", "/usr/local/tomcat/webapps/ROOT"]
ADD jenkins.war /usr/local/tomcat/webapps/ROOT.war
ADD context.xml /usr/local/tomcat/conf/context.xml
RUN ["mkdir", "-p", "/usr/local/jenkins"]
ENV JAVA_OPTS="-Djava.awt.headless=true"
ENV CATALINA_OPTS="-DJENKINS_HOME=/usr/local/jenkins/ -Xmx512m"
CMD ["catalina.sh", "run"]