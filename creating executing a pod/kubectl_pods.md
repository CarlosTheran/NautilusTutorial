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

At this point, you don't have any pods on your namespace. Let's create a pod and launch it and check the status of the pod. 
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

* Open a new tab on your brower (firefox, google chrome, ect) and paste the token generated when you launch 
your jupyter nootebook in this case, the token was.
```
http://127.0.0.1:8888/?token=16b3efe8dabecc8fa2264180ae0313d1a543f2de219c3f0a
```
The ouput will be 

![Jupyter](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/jupyter.PNG)

Now, lets create our python notebook. For this you need to *new* and choose **Python3(ipykernel)**
![Jupyter](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/jupyter_python3.png)

Now you are ready to have fun working on you code.
![Jupyter](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/python3.PNG)

**If you are not familiar with working on the terminal, there is the option to launch your container 
and Jupiter notebook using  [Jupyterhub](https://jupyterhub.readthedocs.io/en/stable/)** 

To verify how much resources your jobs are using, to [namespace dashboard](https://grafana.nrp-nautilus.io/d/85a562078cdf77779eaa1add43ccec1e/kubernetes-compute-resources-namespace-pods?orgId=1&refresh=10s&var-datasource=default&var-cluster=&var-namespace=fa) and select your namespace. 

* If you need to quickly run your code on *nautilus* and skip everything related to Kubernetes, you want to use jupyterHub and set the specs of your containers (GPUs, Cores, RAM, GPU type, and image)
easily on nautilus, do the following instructions.

If you are located in the east of the USA, create your account on [jupyterhub-east](https://jupyterhub-east.nrp-nautilus.io/hub/login). Otherwise,  if you are located in the west of the USA use [jupyterhub-west](https://jupyterhub-west.nrp-nautilus.io/hub/login?next=%2Fhub%2F). For new users,  you need to request access in the [matrix](https://element.nrp-nautilus.io/#/room/#general:matrix.nrp-nautilus.io) using your institutional credentials to login using CILogon. If the domain of your institutional email is not on the system, they will be at your institution domain. For example, for juandel.pueblo@upr.edu or juandel.pueblo@famu.edu they will add the domain *upr* or *famu*. 

![Jupyterhub](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/jupytherhub.PNG)


Once get access is provided, you are allowed to create your containers. There is a restriction, *Your persistent home folder initially will be limited to 5GB. If you need more, you can request it to be extended.*

![Jupyterhub_container](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/jupyterhub_containers.PNG)

When you select the requirements and image for your pod, the server will start pulling the image you selected. In this
particular case the image selected was **Datascience**

![Jupyterhub_container_launched](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/jupytherhub_lunched.PNG)

Finally, if you want to see all the images provided by nautilus you must to create an [GitLab account](https://gitlab.nrp-nautilus.io/users/sign_in). Then, you will be able to see the [Container Registry](https://gitlab.nrp-nautilus.io/prp/jupyter-stack/container_registry/)

Now that we can create and execute pods on **nautilus**, let's run an [example](https://github.com/CarlosTheran/NautilusTutorial/tree/main/example). 