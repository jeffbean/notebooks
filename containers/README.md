**<h1>NOTE: These are notes not a dictionary for the topic.</h1>**

# The New world
I would recommend reading up on the technology first.
* [Docker](http://docs.docker.com/index.html)
* [Linux Containers](https://linuxcontainers.org)
* [Go](https://golang.org)


## What is going on?
Section is meant to be notes on what to look into near future.
* [Open Container Project](http://www.opencontainers.org)
* [Windows Containers](http://blogs.technet.com/b/server-cloud/archive/2015/04/08/microsoft-announces-new-container-technologies-for-the-next-generation-cloud.aspx)
* [Cloud Native Foundation](http://www.linuxfoundation.org/news-media/announcements/2015/07/new-cloud-native-computing-foundation-drive-alignment-among)


## Breaking it down

### Container Host Operating systems

Before we can run Docker or any other container we need to first have a OS that runs containers. Most Linux distributions support Docker but are also bloated with extra packages that are not necessary. A new set of Operating systems have now been created specifically for container workloads.


The premise of the container OS is to have the lightest host OS footprint so you can run purely containers on the host. Many of them come pre-installed and configured out of the box so you don't have to worry about bootstrapping an OS with many of the tools you need to run a containerized workload.

* [CoreOS](https://coreos.com)
* [Atomic](http://www.projectatomic.io)
* [RancherOS](https://github.com/rancher/os)
* [VMWare Photon](https://github.com/vmware/photon)


## container engine (runtime)

The tool that actually runs the containers is referred to as the container engine. Today there are many flavors of an engine but the most popularized is Docker.

Docker donated to the Open Container Project the container engine from Docker and is now called [runc](https://github.com/opencontainers/runc) that could become the standard across all the different tools. This would mean that all container engines could then run any other engines images. A single format for all.

 The following are the current container engines.

* [Docker](https://www.docker.com/)
* [rkt](https://github.com/coreos/rkt)
* [appc](https://github.com/appc/spec)
* [runc](https://github.com/opencontainers/runc)

## images
Images are what containers are made from. You build ship and run the images for the container engine. The container engine then runs and manages that now running container.

## networking
To be filled

## storage
To maintain persistence there are two main ways to do this.

One is to configure a persistent data volume or container. This is a common pattern and is illustrated and documented by Docker [here](https://docs.docker.com/userguide/dockervolumes/).

The second way is to rewrite or, more commonly, start fresh writing the software to a persistence layer outside of the container system. Things like S3 endpoints or more commonly now “etcd” or Cassandra DB’s that are clustered and maintain state within a cluster, allowing you to persist within a cluster of nodes.

Kubernetes has a concept of configuring persistent storage. You first declare what volumes are available, then each pod you create can access these volumes. A good doc for this can be found [here](http://kubernetes.io/v1.0/examples/mysql-wordpress-pd/README.html ).



## orchestration
Once you start using containers for more than just dev/test it will become necessary to have orchestration.

* [Kubernetes](http://kubernetes.io)


# Blogs and Slidedecks
* [Kubernetes explains container design patterns](http://blog.kubernetes.io/2015/06/the-distributed-system-toolkit-patterns.html)


## Dockercon15
* Good overall talk. MUST WATCH [Adrien Cockcraft](https://www.youtube.com/watch?v=zDuTIZBh5_Q&list=PLkA60AVN3hh94tm0_6_rGxamkuHOLr30l&index=12)
* Great talk on definitions [Resilient Routing and Discovery](https://www.youtube.com/watch?v=ZDeAEZHby_A&list=PLkA60AVN3hh94tm0_6_rGxamkuHOLr30l&index=15)
* The [Keynote Day 1](http://www.slideshare.net/Docker/dockercon-sf-2015-keynote-day-1) has a video embedded. Perfect way to learn about how Docker sees the Docker movement.
* The [Keynote Day 2](http://www.slideshare.net/Docker/dockercon-15-keynote-day-2) includes the panel discussion.
* Good for tech people that are looking to user the Docker registry. [Registry 2](http://www.slideshare.net/Docker/docker-registry-v2)
