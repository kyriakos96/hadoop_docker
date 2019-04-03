# Hadoop Docker Image example

This is a small sample of how to build a Haddop image using Docker.
Credit to [this guide](http://bigdatums.net/2017/11/04/creating-hadoop-docker-image/)

This Dockerfile shows an example of installing Hadoop on Ubuntu 16.04. 
* The start-hadoop.sh script is used to start SSH and Hadoop (contents shown below). 

The Hadoop and SSH configuration files are copied from the local filesystem using the __ADD__ command.

## Building the Docker Image
```
docker build -t my-hadoop .
```

## Creating & Running Docker Container
```
docker run -p 8088:8088 --name my-hadoop-container -d my-hadoop
```

## Accessing Hadoop in Docker Container

```
# start interactive shell in running container
docker exec -it my-hadoop-container bash

# once shell has started run hadoop "pi" example job
hadoop jar $HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-examples-2.8.5.jar pi 10 100
```

