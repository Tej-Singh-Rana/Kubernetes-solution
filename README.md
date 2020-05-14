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
