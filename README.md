# Docker images for Open Source bigdata/hadoop projects

Flokkr is an umbrella github organization to collect all of the containerization work for Apache bigdata/datascience projects such as Apache Hadoop or Apache Spark.

On high level there are two main kind of repositories under the organization. Containers and runtime configuration examples.

### Containers

All of the containers are based on one smart baseimage defined in [flokkr/docker-baseimage](https://github.com/flokkr/docker-baseimage). It contains all the configuration loading script (based on environment variables or consul servers) and other extensions (eg. btrace instrumentation).

All the other containers can be found with [docker-](https://github.com/search?q=org%3Aflokkr+docker) prefix under the flokkr organization.

The containers are usually built on travis-ci and pushed to the docker hub instead to use dockerhub automatic buidls due to the limitation of the dockerhub (for example it's hard to generate matrix builds with all the older versions). 

| Repository                               | Product                                  |
| ---------------------------------------- | ---------------------------------------- |
| [docker-baseimage](https://github.com/flokkr/docker-baseimage) | Base image with all the configuration loading magic |
| [docker-hadoop](https://github.com/flokkr/docker-hadoop) | Apache Hadoop components (hdfs/yarn)     |
| [docker-spark](https://github.com/flokkr/docker-spark) | Apache Spark components                  |
| [docker-zeppelin](https://github.com/flokkr/docker-zeppelin) | Apache Zeppelin interface                |
| [docker-krb5](https://github.com/flokkr/docker-krb5) | Highly insecure kerberos container, with an open REST api to request new kerberos keytab files. |

**Note**: previous version of the containers (and some not yet migrated) can be found under the [github.com/elek](https://github.com/elek) account.

### Runtime

Docker image creation is easy, just a few line to download and unpack the Apache projects. The tricky part is how the containers could work together: service discovery, configuration management, data locality, multi-tenancy, etc.

There are various examples how the containers could be used and each of them have a separated repository with the [runtime](https://github.com/search?q=org%3Aflokkr+docker)- prefix.


| Repository                               | Details                                  |
| ---------------------------------------- | ---------------------------------------- |
| [runtime-compose](http://github.com/flokkr/runtime-compose) | docker-composed based pseudo clusters (multiple containers but only for one hosts). Configuration are defined by environment variables. For development and local experiments. |
| [runtime-consul](http://github.com/flokkr/runtime-consul) | Multi-host real cluster with consul (for storing the configuration and docker-compose definitions) and docker-compose. Small scripts help to maintain the cluster state (restart components on every config change). Full data-locality is achieved by using docker host network. |
| [runtime-swarm](http://github.com/flokkr/runtime-swarm) (WIP) | Similar to the previous one, but the container scheduling part is simplified with docker-compose + swarm. No host network, so no data-locality. Environment variable based configuration management. |
