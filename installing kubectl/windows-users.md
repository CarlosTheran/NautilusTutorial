The following information provides some detailed information about Kubernetes installation for Windowns users.

1. Open a Command Prompt window and downloading kubernetes version *v1.22.0*

``curl -LO "https://dl.k8s.io/release/v1.22.0/bin/windows/amd64/kubectl.exe``

2. Go to your download folder and install *kubectl.exe* from your Command Prompt

``"kubectl.exe"``

![kubectl-install](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/kubectl-install.PNG)

3. Download the kubectl checksum file:

``curl -LO "https://dl.k8s.io/v1.22.0/bin/windows/amd64/kubectl.exe.sha256``

![kubectl-install](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/kubectl-sha.PNG)

4. Using Command Prompt to manually compare CertUtil's output to the checksum file downloaded:

``CertUtil -hashfile kubectl.exe SHA256``

``type kubectl.exe.sha256``

![kubectl-type](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/kubectl-type.PNG)
