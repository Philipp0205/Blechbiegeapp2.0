# Eclipse
[[!Windows]]

---
## Setup 
### Content assist
- Window -> Preferences -> Editor -> Content Assist
 	- `abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ._`
		- Means that it triggers on every char like in other IDEs
	- **Source:** https://stackoverflow.com/questions/6912169/eclipse-enable-autocomplete-content-assist

### Maven project
- Don't forget mvn eclipse:eclipse

### Run config 
```
mvn -u
mvn clean 
javafx:run
```

### Run config neu 
```
--module-path C:\Users\E9T9H13\Development\javafx-sdk-15\lib
--add-modules=javafx.controls,javafx.fxml
```


### Must have plugins
- Vrapper
- Relative line ruler
- codota
- dev style (theme)
- TM Terminal

### Wrong java version error 
- The Java to run Eclipse can be specified in the eclipse.ini file (see Eclipse wiki: eclipse.ini - Specifying the JVM). Add the following two lines directly before the line -vmargs and adapt the path to your Java 11 or higher 64-bit Java VM installation directory:
	- -vm
	- C:\Program Files\AdoptOpenJDK\jdk-14.0.2.12-openj9\bin\javaw.exe

## Debugger failes
 - For some reason just reset perspective... 

## Tipps
- Find next occurance
    - Put the cursor on the word you're looking for
    - Hit alt + shift + up
    - Hit ctrl + k

## Sonar
url: https://highway.porsche.com/sonarqube
Token gibt es im sonarqube acc
Token kann hier generiert weren: https://skyway.porsche.com/sonarqube/account/security

proxy: http-proxy.emea.porsche.biz
port: 3133

kein user auth

## Line wrapping
https://stackoverflow.com/questions/6275785/wrapping-chained-method-calls-on-a-separate-line-in-eclipse-for-java

Complementing Deepak Azad's answer, what you exactly need is the following:

> **Windows**: Window → Preferences → Java → Code Style  
> → Formatter → Edit → Line wrapping (tab)
> 
> **Mac OS**: ADT → Preferences → Java → Code Style  
> → Formatter → Edit → Line wrapping (tab)

Then, in the list at the left, select:

> Function Calls → Qualified invocations

Now below this list, set **Line wrapping policy** to:

> Wrap all elements, except first element if not necessary

**Check**:

> Force split, even if line shorter than maximum line width

Finally, set **Indentation policy** to (thanks [@Turbo](https://stackoverflow.com/questions/6275785/wrapping-chained-method-calls-on-a-separate-line-in-eclipse-for-java#comment16795333_10446098)):

> Indent on column

It should give you the exact behavior you asked for.

### My settings
![[Pasted image 20211124155909.png]]

