# Run Apache Bigdata projects in Kubernetes

Flokkr is a project to run Apache Bigdata projects.

It provides:

 * Ready to use docker containers to run Hadoop/Ozone/Flink/Spark.
 * Example cluster definitions and tests
 * **A powerful, composition-based approach** to generate Kubernetes resource files for different use cases.
 * Toolset to run Bigdata project in the containers

Active repositories to check:

 * Containers are created from `flokkr/docker-*` repositories
 * Resource generation is based on https://github.com/elek/flekszible tool (Think about Kustomize on steriod)
 * Kustomize based cluster definition can be found:
   * https://github.com/flokkr/k8s: Main repository with all the K8s definitions
   * https://github.com/flokkr/infra-flekszible: Independent monitoring/logging as addition to the clusters
   * https://github.com/flokkr/ozone-flekszible: Dedicated defitions for Apache Hadoop Ozone
 * The last three repositories can be used with [flekszible](https://github.com/elek/flekszible) to generate any cluster setup (and deploy it with existing k8s tools)
 * https://github.com/flokkr/demo repository contains ready-to-use example cluster defintions (easy to customize with flekszible) with different components (Spark + Yarn, Flink + Kafka, Ozone + Spark, ...)

For more information, check https://github.flokkr.iot
