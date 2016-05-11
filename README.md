# Glusterfs Kubernetes Cluster Sidecar

This project is as a PoC to setup a gluster cluster using Kubernetes. It should handle resizing of any type and be
resilient to the various conditions both gluster and kubernetes can find themselves in.

## How to use it

The docker image is hosted on docker hub and can be found here:  
https://hub.docker.com/r/neshte/gluster-k8s-sidecar/

An example kubernetes replication controller can be found in the examples directory on github here:  
https://github.com/neshte/gluster-k8s-sidecar

There you will also find some helper scripts to test out creating the cluster and resizing it.

### Settings

- GLUSTER_SIDECAR_POD_LABELS  
  Required: YES  
  This should be a be a comma separated list of key values the same as the podTemplate labels. See above for example.
- GLUSTER_SIDECAR_SLEEP_SECONDS  
  Required: NO  
  Default: 5  
  This is how long to sleep between work cycles.
- GLUSTER_SIDECAR_UNHEALTHY_SECONDS  
  Required: NO  
  Default: 15  
  This is how many seconds a cluster member has to get healthy before automatically being removed from the cluster.
- GLUSTER_SIDECAR_CLUSTER_NAME  
  Required: NO  
  Default: glusterfs-cluster  
  This is the meta.name of the kubernetes endpoints.
- GLUSTER_SIDECAR_CLUSTER_PORT  
  Required: NO  
  Default: 1  
  This is the cluster port for kubernetes gluster volume mounting.

## Debugging

TODO: Instructions for cloning, mounting and watching

## Still to do

- Add tests!
- Add to circleCi
- Alter k8s call so that we don't have to filter in memory

## Inspired in

This sidecar is inspired in a sidecar for mongo with kubernetes
https://github.com/leportlabs/mongo-k8s-sidecar
