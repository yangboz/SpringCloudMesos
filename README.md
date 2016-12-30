# SpringCloudMesos
High Available SpringCloud eureka service discovery on Mesos

# How to run on MacOSX
You have to install Zookeeper and Mesos, also need Marathon. I assume you have java and homebrew installed.

```
brew install zookeeper
brew install mesos
```

That was the complete installation.

1.Now start Zookeeper
```
zkServer start
```
Start a Mesos master :

```
/usr/local/sbin/mesos-master --registry=in_memory --ip=192.168.0.11 --zk=zk://192.168.0.11:2181/jpoint-mesos --work_dir=~~/mesos/workdir
```

Note that I use my network-ip in the configuration. It’s possible with localhost but on a Mac.

You sometimes run into trouble with localhost/127.0.0.1/0.0.0.0/hostname and you eventually will have more than one cluster node,

so it will save you time in the end to do it right from the start.

jpoint-mesos is the location in zookeeper where the information about the cluster is stored, it can be anything but / and will be automatically created.

After the logging cools down you should see a console at : http://192.168.0.11:5050

Now it’s time to start a slave :

```
/usr/local/sbin/mesos-slave --master=zk://192.168.1.21:2181/jpoint-mesos
```

When you start a slave it should appear in the web console : http://192.168.0.11:5050/#/slaves

# References

http://container-solutions.com/writing-mesos-framework-scratch-mesos-starter/

http://dockone.io/article/1702

https://vanwilgenburg.wordpress.com/2015/05/10/how-to-run-a-spark-cluster-on-mesos-on-your-mac/

# TODO:

http://blog.csdn.net/zhuchuangang/article/details/51295380
