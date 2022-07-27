#lecture-note
[[1Projects/SE2/02_BuildMangament/Exercise.pdf]]
[[SWE2-BuildManagement-new.pdf]]

---
# Build Management Summary 
## Difference Maven Gradle 
**build.xml and build.gradle**
Gradles *build.gradle* is a DSL based on Groovy which was invented to ditch the verbosity of XML and write more simple and clear statements. 



![[GradleDSLExample.png]]

The gradle DSL is avilable for Groovy and Kotlin.

## Ant 
*build.xml*
```xml
<project name="MyProject" default="dist" basedir=".">
	<description>
		simple example build file
	</description>
	
	<!-- set global properties for this build -->
	<property name="src" location="src"/>
	<property name="build" location="build"/>
	<property name="dist" location="dist"/>
	
	<target name="init">
		<!-- Create the time stamp -->
		<tstamp/>
		<!-- Create the build directory used by compile -->
		<mkdir dir="${build}"/>
	</target>
	
	<target name="compile" depends="init" description="compile the source " >
		<!-- Compile code from ${src} into ${build} -->
		<javac srcdir="${src}" destdir="${build}"/>
	</target>
	
	<target name="dist" depends="compile"
		description="generate the distribution" >
		<!-- Create the distribution directory -->
		<mkdir dir="${dist}/lib"/>
		<!-- Put everything in ${build} into the 
		MyProject-${DSTAMP}.jar file -->
		
		<jar jarfile="${dist}/lib/MyProject-${DSTAMP}.jar" basedir="${build}"/>
	</target>
	
	<target name="clean" description="clean up" >
		<!-- Delete ${build} and ${dist} dirs -->
		<delete dir="${build}"/>
		<delete dir="${dist}"/>
	</target>
</project>	
```

Is composed of any number of *targets*. Each target is composed of *tasks*. 

### Create Ant custom task 
![[AntCustomTask.png]]

## Maven 
Maven is based on Ant. 
Can do everything ant does. 
Adds abstraction layer. 

**Weak Points of ant are:** 
- Bad-Cross-Project-Reuse 
- No support for conditional logic / loops
- handling with libraries
- No defined build lifecyle

**How Maven addresses these problems**

*Plug-In-Concept*
Definition of reusable, project-independent gials

*Project Object Model (POM)*
Description of project 

*Repository Concept*
Maven builds up an own local repository
Maven uses remote-repositories to load libraries. 

### Maven Build-Lifecycle
![[MavenBuildLifecycle.png]]

### Elements of Maven 
![[ElementsOfMaven.png]]

*Transitive dependencies*
Every component knows on what other compnents it depends.

## Gradle 
![[GradleBuildExample.png]]

### Benefits 
*Declarative builds and build-by-convention*
DSL based on Groovy
build-by-convention support for Java, Groovy, Scala

*Language for dependency based programming*

*Gradle scales*
Gradle scales well. With the incremental build function, this is also true for tackeling the performane pain many large enterprise build suffer from.  

*Many ways to manage dependencies*

## Continuous Integration
### CI in the cloud 
*Problem*
Integrating large sofware-system temporarily needs a huge amount of computing power. 
Huge costs, to achieve short integration time.

*Solution*
Run continuous integration in the cloud. 
Only pay for computing power when needed. 
Tools that are used inside the build pipeline usually can be chosen.



