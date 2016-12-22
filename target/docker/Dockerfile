#使用daocloud的java8镜像
FROM daocloud.io/library/java:8
#镜像创建人
MAINTAINER yangboz
#附加卷
VOLUME /tmp
#添加jar包
ADD eip-spring-cloud-mesos-0.0.1-SNAPSHOT.jar app.jar
#修改jar包日期
RUN bash -c "touch app.jar"
#运行app,并指定端口号
ENTRYPOINT java -Djava.security.egd=file:/dev/./urandom -jar /app.jar --server.port=$PORT0