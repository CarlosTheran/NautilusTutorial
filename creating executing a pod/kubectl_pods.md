# Creating and executing a pod (kubectl commands).
* list of cluster node executed on Nautilus
```
kubectl get nodes
```
* To list the **node = <pods, deployments, services, jobs>** that are attached to your namespace 
```
  kubectl get pods node
```
change the word node by one the modality defined as node.

At this point, you don't have any pods on your namespace. Let's create a pod and lunch it and check the status of the pod. 
To create a pod, we need to follow a structured file save as yaml extension. Lets create folder called pods
```
  mkdir pods
```

* Before to start creating and executing your pods check that you are in the corret *NAMESPACE*
```
kubectl config get-contexts
```
The output must be like this
```
CURRENT   NAME       CLUSTER    AUTHINFO                                    NAMESPACE
*         nautilus   nautilus   http://cilogon.org/serverA/users/51474921   <YOUR NAME SPACE>
```

Please download the file [tensorflow-pod](https://github.com/CarlosTheran/NautilusTutorial/blob/main/creating%20executing%20a%20pod/tensorflow-pod.yaml)
, which is an example of a *pod* and save it on your pods folder.

* Let's create our pod with the requirements established in  *tensorflow-pod*

```
kubectl create -f tensorflow-pod.yaml
```

* Verify the status of your pods
```
kubectl get pods
```
You must get somethign like this:
```
NAME              READY   STATUS    RESTARTS   AGE
gpu-pod-example   1/1     Running   0          34s
```

Sometimes create your pod take times, in this case you will see the STATUS as *CreatingContainer*.   
* Now that your pod is running, let's execute this pod to get into it.
```
kubectl exec -it gpu-pod-datascience -- /bin/bash
```
The output of this command must the following. Which mean that you are into your container or pod

```
(base) jovyan@gpu-pod-example:~$
```
* The following commands are use to see the specs of you pod.

```
(base) jovyan@gpu-pod-example:~$ uname
(base) jovyan@gpu-pod-example:~$ uname --m
(base) jovyan@gpu-pod-example:~$ uname -o
(base) jovyan@gpu-pod-example:~$ lscpu
```