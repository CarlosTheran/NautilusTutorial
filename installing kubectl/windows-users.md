The following information provides some detailed about Kubernetes installation for Windowns users.

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

5. Using PowerShell to automate the verification using the -eq operator to get a True or False result:

``$($(CertUtil -hashfile .\kubectl.exe SHA256)[1] -replace " ", "") -eq $(type .\kubectl.exe.sha256)``

6. Add the binary in to your PATH.
    * Create a new folder, you can named it as you want.For example, *kubernet*.
    * Copy the file download in step 1 and paste it into the new folder.
    * Go to **Advance system setting**

    ![system-properties](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/system-properties.PNG)

    * Click on **Enviroment Variable**
    ![environment-varialbes](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/environment-variable.PNG)

    * Click on **path** from User variable for Windowns. Add path for kubernet, click on **Edit** 
    ![add-path](https://github.com/CarlosTheran/NautilusTutorial/blob/main/img/add-path.PNG)