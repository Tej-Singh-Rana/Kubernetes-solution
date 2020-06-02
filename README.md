# Kubernetes-solution
> Kubernetes > Control-plane > Worker-node > Cloud-platform
# Follow these steps to make an alias :-
  1. source <(kubectl completion bash)
  2. alias k=kubectl
  3. complete -F __start_kubectl k

> Pod task :-
```
> Performed in kubectl = v1.16

> In k8s, v1.18 by run command it will create Pod instead of Deployment.

> Create Pod && Deployment

kubectl run busybox-test --image=busybox --labels="my-label=test,run=busybox" --restart Never -- sh -c "hostname > /tmp/hostname && sleep 1d"

> To exec Pod's container

kubectl exec -it busybox-test cat /tmp/hostname

> To replace old one, it will delete and re-create new Pod.

kubectl replace -f pod.yml --force

> To add labels in run time

kubectl label pod <pod-name> key1=value1

> To delete Pod forcefully 

kubectl delete pod <pod-name> --force --grace-period=0
```
# PodNodeSelector

- To assign into a particular node, We will use PodNodeSelector object.

```
$ cd /etc/kubernetes/manifests

$ vi kube-apiserver.yaml

> Added PodNodeSelector into  --enable-admission-plugins=PodNodeSelector
> After this kube-apiserver automatically restarted.

> Assigning label to node01 
$ kubectl label node node01 -l="server=first"

> We have to create namespace and add "annotations" column to find particular label in the cluster.

$ kubectl create namespace test

$ kubectl edit namespace test
> Add following parameters in metadata section.

> annotations:
    scheduler.alpha.kubernetes.io/node-selector: "server=first"

> After this create a deployment or pod in that newly created namespace. Pod will be schedule after matching labels in particular node.


