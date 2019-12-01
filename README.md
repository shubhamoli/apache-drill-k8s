# **Apache drill | K8s**


This is a demostration of deploying Apache Drill and ZooKeeper on K8s as statefulsets.


## Files

* apache-drill.yml
* zookeeper.yml 

## Images

* Apache drill - https://hub.docker.com/r/olishubham/apache-drill (v1.15.0)
* Zookeeper - https://hub.docker.com/_/zookeeper/ (v3.4.14)


## Architecture

* Namespaces -

    * `apache-drill` (for apache drill resources)
    * `zookeeper`    (for all zookeeper resources)

* Headless services - 

    * `apache-drill-headless-svc`
    * `zookeeper-headless-svc`

* Services - 

    * `apache-drill-svc` (:8047)
    * `zookeeper-svc`    (:2181)

* PodDisruptionBudget - 1 pod at a time

* Pod Anti-affinity - deploy pods in different node (HA practice)

* Pod Scheduling - Ordered (default for statefulsets)

* Pod Security Context - run as uid/gid 1000 (both deployments)

* Persistent Volumes - as it is tested on minikube so **no dynamic provisioning** of volumes
