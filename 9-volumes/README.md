# Kubernetes Storage 
### On-disk files in a container are ephemeral, which presents some problems for non-trivial applications when running in containers. One problem is the loss of files when a container crashes. The kubelet restarts the container but with a clean state. A second problem occurs when sharing files between containers running together in a Pod. The Kubernetes volume abstraction solves both of these problems. Familiarity with Pods is suggested.

### Things to consider while giving storage solution to Kubernetes:

- Storage that doesn’t depend on the pod lifecycle
- Storage must be available on all the nodes
- Storage should survive even after the cluster crashes

### Kubernetes supports several types of volumes, this exercise talks about awsElasticBlockStore and local storage

**pre-requisites**
- Must have kubernetes cluster, Good to create with AWS EKS
- Must have some knowledge about POD's and deployments


### Use following link to create volumes with AWS EFS https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html