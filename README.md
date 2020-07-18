# Eclipse
## Plug-ins
- [Spring Tools] (https://spring.io/tools)
- [SonarLint for Eclipse] (http://www.sonarlint.org/eclipse/)
- [Project Lombok] (https://projectlombok.org/)

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
"editor.fontFamily": "'Cascadia Code PL', Consolas, 'Courier New', monospace"
"java.format.settings.url": "https://raw.githubusercontent.com/zhoozhoo/eclipse/master/formatter.xml"
"java.format.enabled": true
```

# WSL 2

## .wslconfig

## AdoptOpenJDK
```
wget -qO - https://adoptopenjdk.jfrog.io/adoptopenjdk/api/gpg/key/public | sudo apt-key add -
sudo add-apt-repository --yes https://adoptopenjdk.jfrog.io/adoptopenjdk/deb/
sudo apt-get update 
sudo apt-get install adoptopenjdk-14-hotspot
```
## Maven
```
sudo apt-get update 
sudo apt-get install maven
```
