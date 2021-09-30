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

* Let's create our pod with the requirements established in  *tensorflow-pod*. Please download the file [tensorflow-pod](https://github.com/CarlosTheran/NautilusTutorial/blob/main/creating%20executing%20a%20pod/tensorflow-pod.yaml)
, which is an example of a *pod* and save it on your pods folder.

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
```
```
(base) jovyan@gpu-pod-example:~$ uname --m
```
```
(base) jovyan@gpu-pod-example:~$ uname -o
```
```
(base) jovyan@gpu-pod-example:~$ lscpu
```
* Now that you are into the container, you can luch a jupyter note book
```
jupyter notebook --ip='0.0.0.0'
```
The output must looks like this
```
[I 19:39:29.307 NotebookApp] Writing notebook server cookie secret to /home/jovyan/.local/share/jupyter/runtime/notebook_cookie_secret
[W 2021-09-30 19:39:31.035 LabApp] 'ip' has moved from NotebookApp to ServerApp. This config will be passed to ServerApp. Be sure to update your config before our next release.
[W 2021-09-30 19:39:31.035 LabApp] 'port' has moved from NotebookApp to ServerApp. This config will be passed to ServerApp. Be sure to update your config before our next release.
[W 2021-09-30 19:39:31.036 LabApp] 'port' has moved from NotebookApp to ServerApp. This config will be passed to ServerApp. Be sure to update your config before our next release.
[W 2021-09-30 19:39:31.036 LabApp] 'port' has moved from NotebookApp to ServerApp. This config will be passed to ServerApp. Be sure to update your config before our next release.
[I 2021-09-30 19:39:31.044 LabApp] JupyterLab extension loaded from /opt/conda/lib/python3.9/site-packages/jupyterlab
[I 2021-09-30 19:39:31.044 LabApp] JupyterLab application directory is /opt/conda/share/jupyter/lab
[I 19:39:31.049 NotebookApp] Serving notebooks from local directory: /home/jovyan
[I 19:39:31.049 NotebookApp] Jupyter Notebook 6.4.0 is running at:
[I 19:39:31.049 NotebookApp] http://gpu-pod-example:8888/?token=16b3efe8dabecc8fa2264180ae0313d1a543f2de219c3f0a
[I 19:39:31.049 NotebookApp]  or http://127.0.0.1:8888/?token=16b3efe8dabecc8fa2264180ae0313d1a543f2de219c3f0a
[I 19:39:31.049 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 19:39:31.054 NotebookApp]

    To access the notebook, open this file in a browser:
        file:///home/jovyan/.local/share/jupyter/runtime/nbserver-57-open.html
    Or copy and paste one of these URLs:
        http://gpu-pod-example:8888/?token=16b3efe8dabecc8fa2264180ae0313d1a543f2de219c3f0a
     or http://127.0.0.1:8888/?token=16b3efe8dabecc8fa2264180ae0313d1a543f2de219c3f0a
```
* In a new command prompt or terminal run the following command
 ```
kubectl port-forward gpu-pod-example 8888:8888
 ```

 The output must be like this
```
Forwarding from 127.0.0.1:8888 -> 8888
Forwarding from [::1]:8888 -> 8888
```