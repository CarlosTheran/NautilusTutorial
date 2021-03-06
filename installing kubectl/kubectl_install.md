To launch your Pods, Jobs and Deployments using the platform's resources you need to install The Kubernetes command-line tool [kubectl](https://kubernetes.io/docs/tasks/tools/).

kubectl is installable on a variety of Linux platforms, macOS and Windows. Find your preferred operating system below. 
* [linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
* [macOS](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
* [windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)

Note: You can find and get the binary file that you need [here](https://www.downloadkubernetes.com/).

For windows user check the following steps [Installetion-Steps](https://github.com/CarlosTheran/NautilusTutorial/blob/main/installing%20kubectl/windows-users.md).

Now, get into your portal and click on ![GetConfig](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/get_config.PNG)
Save the file as config and put the file in your /.kube folder. This folder may not exists on your machine, to create it execute: 
```
  mkdir ~/.kube
```
Create an namespace on your portal. then, test the connection of your namespace using *kubectl* on command prompt, terminal, or PowerShell.
```
  kubectl get pods -n your_namespace
```

For more information and details visit [Quick Start](https://ucsd-prp.gitlab.io/userdocs/start/quickstart/). Now, lets create our [first Pod](https://github.com/CarlosTheran/NautilusTutorial/blob/main/creating%20executing%20a%20pod/kubectl_pods.md).


