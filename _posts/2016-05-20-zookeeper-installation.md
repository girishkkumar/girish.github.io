---
layout: post
title: "Zookeeper Installation"
date: 2016-05-20
---
* * *
To install ZooKeeper framework on your machine, visit the following link and download the latest version of ZooKeeper. 
* * *
[Zookeeper Download Link](http://zookeeper.apache.org/releases.html)


Extract the tar file using the following commands −
``
$ cd /home/<user>/
$ mkdir zookeeper
$ cd zookeeper
$ tar zxvf zookeeper-3.4.8.tar.gz
$ cd zookeeper-3.4.8
``
The location where the ZooKeeper archive is extracted in our case, /home/***user***/zookeeper/zookeeper-3.4.8 , can be exported as ZK_HOME as follows:

```
$ cd /
$ sudo vi ~/.bashrc
```
Add the below lines in bashrc file 
```
export ZK_HOME=/home/<user>/zookeeper/zookeeper-3.4.8
export PATH=$PATH:$ZK_HOME/bin
```
save the bashrc file and source it.
```
$ source ~/.bashrc
```

To start the servers individually run the below commands
```
$ cd /zookeeper-3.4.8/bin
$ ./zkServer.sh start ../conf/zoo1.cfg
$ ./zkServer.sh start ../conf/zoo2.cfg
$ ./zkServer.sh start ../conf/zoo3.cfg
```

It is possible to check whether a ZooKeeper server is a leader or follower using the nc command that is included in the netcat package:
```
echo srvr | nc localhost 2181 | grep Mode
```

If the ZooKeeper server is a leader then the command will return: Mode: leader and otherwise: Mode: follower


To stop the servers individually run the below commands
```
$ cd /zookeeper-3.4.8/bin
$ ./zkServer.sh stop ../conf/zoo1.cfg
$ ./zkServer.sh stop ../conf/zoo2.cfg
$ ./zkServer.sh stop ../conf/zoo3.cfg
```


persistent znode
----------------------
persistent znodes have a lifetime in the ZooKeeper's namespace until they're explicitly deleted. A znode can be deleted by calling the delete API call
