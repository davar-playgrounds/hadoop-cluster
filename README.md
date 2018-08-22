# Hadoop Cluster

We created small [hadoop][hadoop] cluster for tests.

## Architecture of a Hadoop Cluster

Before we start, we have to understand different components of [hadoop][hadoop] cluster.

Basically we have two main components:

- [HDFS](http://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsDesign.html)
- [YARN](http://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html)

## HDFS
-----------------------------

HDFS_ is a distributed file system designed to run on commodity hardware and has master/slave architecture.

**NameNode** is a single node that manages the file system namespace and regulates access to files by clients.
There are also many **DataNodes** which manage storage attached to the nodes that they run on.

## YARN
-----------------------------

YARN_ - splits up the functionalities of resource management and job scheduling/monitoring into separate daemons.

**ResourceManager** is the ultimate authority that arbitrates resources among all the applications in the system.

**NodeManager** is the per-machine framework agent who is responsible for containers,
monitoring their resource usage (cpu, memory, disk, network) and reporting the same to the ResourceManager/Scheduler.


## How to use image?

By default you don't need to do anything except run image:

```
docker run -it robloj/centos-tensorflow-bazel
```

When image is downloaded, you can check if bazel exists:

```
root@39f0849fe655:/# bazel version

WARNING: --batch mode is deprecated. Please instead explicitly shut down your Bazel server
using the command "bazel shutdown".
Build label: 0.15.1
Build target: bazel-out/k8-opt/bin/src/main/java/com/google/devtools/build/lib/bazel/BazelServer_deploy.jar
Build time: Mon Jul 16 14:16:24 2018 (1531750584)
Build timestamp: 1531750584
Build timestamp as int: 1531750584
```

That's all. Now you can use bazel.

## How to build my own bazel image?

If you want to build your own bazel image, you have to provide bazel and gcc
versions. For example:

```
docker build --build-arg BAZEL_VER=0.15.1 -t my-tensorflow-bazel .
```

Where:

- BAZEL_VER - [bazel](https://docs.bazel.build/) version you want to use


[hadoop]: http://hadoop.apache.org/
