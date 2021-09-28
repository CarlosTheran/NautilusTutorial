To lunch your Pods, Jobs and Deployments using the platform's resources you need to install The Kubernetes command-line tool [kubectl](https://kubernetes.io/docs/tasks/tools/).

kubectl is installable on a variety of Linux platforms, macOS and Windows. Find your preferred operating system below.
* [linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
* [macOS](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
* [windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)

Now, get into your portal and click on ![GetConfig](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/get_config.PNG). Save the file as config and put the file in your /.kube folder. This folder may not exists on your machine, to create it execute: 
```
  mkdir ~/.kube
```