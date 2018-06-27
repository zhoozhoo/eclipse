# My Eclipse Configuration
## Plug-ins
- [Spring Tool Suite™] (https://spring.io/tools/sts)
- [Spring Tool Suite 4] (https://github.com/spring-projects/sts4/wiki/Installation)
- [SonarLint for Eclipse] (http://www.sonarlint.org/eclipse/)
- [Papyrus] (http://www.eclipse.org/papyrus/)
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
-javaagent:lombok.jar
```
