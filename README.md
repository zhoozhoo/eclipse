# Eclipse

## Plug-ins

- [Spring Tools](https://spring.io/tools)
- [SonarLint for Eclipse](http://www.sonarlint.org/eclipse/)
- [Project Lombok](https://projectlombok.org/)

## eclipse.ini

```ini
...
-vm
%JAVA_HOME%/bin/server/jvm.dll
-vmargs
...
```

# Visual Studio Code

```json
"terminal.integrated.fontFamily": "Cascadia Code PL"
"terminal.integrated.fontSize": 12
"java.format.settings.url": "https://raw.githubusercontent.com/zhoozhoo/eclipse/master/formatter.xml"
"java.format.enabled": true
```

# WSL 2

## Update the `sudoers`

```bash
# Edit the sudoers with the visudo command
sudo visudo

# Change the %sudo group to be password-less
%sudo ALL=(ALL:ALL) NOPASSWD: ALL

# Press CTRL+X to exit
# Press Y to save
# Press Enter to confirm
```

## Install [Midnight Commander](https://midnight-commander.org/)

```bash
sudo apt-get update 
sudo apt-get install mc
```

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
sudo apt-get update 
sudo apt-get install httpie
```

## Install [Helm](https://helm.sh/)

```bash
curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
sudo apt-get install apt-transport-https --yes
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
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
# Create a new ServiceAccount
kubectl apply -f - <<EOF
apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user
  namespace: kubernetes-dashboard
EOF
# Create a ClusterRoleBinding for the ServiceAccount
kubectl apply -f - <<EOF
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: admin-user
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
- kind: ServiceAccount
  name: admin-user
  namespace: kubernetes-dashboard
EOF
# Get the Token for the ServiceAccount
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')
# Copy the token and copy it into the Dashboard login and press "Sign in"
```

# Miscellaneous

## Install Root Certificates in JDK

```bash
cd /usr/lib/jvm/adoptopenjdk-15-hotspot-amd64/lib/security
sudo keytool -import -trustcacerts -file <path to certificate> -alias <alias> -cacerts
```

## Change Default JDK

```bash
update-java-alternatives --list
sudo update-java-alternatives --set <path to jdk>
```
