# Eclipse
## Plug-ins
- [Spring Tools](https://spring.io/tools)
- [SonarLint for Eclipse](http://www.sonarlint.org/eclipse/)
- [Project Lombok](https://projectlombok.org/)

## eclipse.ini
```
.
.
.
-vm
%JAVA_HOME%/bin/server/jvm.dll
-vmargs
.
.
.
```

# Visual Studio Code
```
"terminal.integrated.fontFamily": "Cascadia Code PL"
"terminal.integrated.fontSize": 12
"java.format.settings.url": "https://raw.githubusercontent.com/zhoozhoo/eclipse/master/formatter.xml"
"java.format.enabled": true
```

# WSL 2
## Update the sudoers
```bash
# Edit the sudoers with the visudo command
sudo visudo

# Change the %sudo group to be password-less
%sudo   ALL=(ALL:ALL) NOPASSWD: ALL

# Press CTRL+X to exit
# Press Y to save
# Press Enter to confirm
```

## Update Ubuntu
```bash
# Update the repositories and list of the packages available
sudo apt update
# Update the system based on the packages installed > the "-y" will approve the change automatically
sudo apt upgrade -y
```

## .wslconfig

## Install Powerline
[Tutorial: Set up Powerline in Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/tutorials/powerline-setup)

## Install [Cascade Code](https://github.com/microsoft/cascadia-code/releases) Font

## Install [AdoptOpenJDK](https://adoptopenjdk.net/)
```bash
wget -qO - https://adoptopenjdk.jfrog.io/adoptopenjdk/api/gpg/key/public | sudo apt-key add -
sudo add-apt-repository --yes https://adoptopenjdk.jfrog.io/adoptopenjdk/deb/
sudo apt-get update 
sudo apt-get install adoptopenjdk-14-hotspot
```

## Install [Maven](https://maven.apache.org/)
```bash
sudo apt-get update 
sudo apt-get install maven
```

## Install [HTTPie](https://httpie.org/)
```bash
sudo apt install httpie
```

## Install [KinD](https://kind.sigs.k8s.io/)
```bash
# Download the latest version of KinD
curl -Lo ./kind https://github.com/kubernetes-sigs/kind/releases/download/v0.8.1/kind-$(uname)-amd64
# Make the binary executable
chmod +x ./kind
# Move the binary to your executable path
sudo mv ./kind /usr/local/bin/
```

## Install [Kubernetes Dashboard](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)
```bash
# Install Kubernetes Dashboard
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.3/aio/deploy/recommended.yaml
# Edit kubernetes-dashboard service - Change type: ClusterIP to type: NodePort
kubectl -n kubernetes-dashboard edit service kubernetes-dashboard
# Check port on which Dashboard was exposed
kubectl -n kubernetes-dashboard get service kubernetes-dashboard
```
