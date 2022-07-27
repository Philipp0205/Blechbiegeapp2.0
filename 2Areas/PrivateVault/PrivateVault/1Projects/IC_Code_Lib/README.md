# IC-Code
> Simplification of Prcodes and returen it as an IC-Code.

## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Setup](#setup)
* [Usage](#usage)
* [Project Status](#project-status)
* [Room for Improvement](#room-for-improvement)
* [Acknowledgements](#acknowledgements)
* [Contact](#contact)
	

## General Information
- IC-Code is a boolean expression with a special syntax that defines on which car configurations a part (or harness / connector) should be built into a car.
- The simplification algorithm tries to simplify IC-Codes to a smaller representation.
- Some set operations have been requested by the customer.

 - __isSubset__ _Checks the given PR-Number codes for equality._
 - __getSymmetricDifference__ _Gets the symmetric difference of two PR-Number    codes._
 - __getSetDifference__ _Checks whether the given PR-Number codes do have an intersection. This is the case if there is at least one vehicle configuration for which each PR-Number code is valid._
 - __getIntersection__ _Gets the intersection for a number of PR-Number codes in form of an IC-Code. The generated IC-Code is valid for each vehicle configuration for which each PR-Number code is valid._
 - __getFastIntersection__ _Gets the intersection for a number of PR-Number codes in form of an IC-Code. The generated IC-Code is valid for each vehicle configuration 
   for which each PR-Number code is valid. The resulting IC-Code won't be simplified._
 - __calculateICCode__ _Calculates an IC-Code by combining the PR-Number keys with an OR-Operation._
 - __validate__ _Validates the given PR-Number code. The validate method executes multiple checks on the given PR-Number code._

   1. Checks the syntax for errors
   2. Checks each PR-Numbers of the PR-Number code if it is in the PR-Data at all
   3. Checks each PR-Numbers of the PR-Number code if it is in the PR-Data initialized with the TMA begin and end date.
 
- A simplified representation is desired.
- There are some use cases which takes too much time in case of implementation. Therefore the purpose is to investigate the issue of use cases and optimize them.


## Technologies Used
- Tech 1 - IntelliJ IDEA   2021.2.2
- Tech 2 - jdk8u version   172-b11
- Tech 3 - Maven: junit    4.12
- Tech 4 - VisualVM        2.1.1


## Setup
- Clone the IC-Code project with [Skyway Porsche](https://skyway.porsche.com/confluence/pages/viewpage.action?pageId=204432120)
- Use JDK8 to run the project

 
- Iccode-lib consists of three folders: iccode-core, iccode-library, iccode-library-api.

- Each folder has its own pom.xml file, each individual pom.xml should be added as a maven project(right click on pom.xml > add as a Maven project)

- Import SDKs:
    - File > Project Structure > SDKs > + (add the jdk8u).
    - File > Project Structure > Project > Project SDK: > choose the jdk8u.
    - File > Project Structure > Project > Project language level: choose SDKdefault(8 - Lambdas ...).
    - File > Project Structure > Modules > for each folder > Module SDK: choose 1.8 version 1.8.

- Build the project in this order core, api, library, javadoc. Since we have three pom.xml file in each folder we need to build them separately.

    - Add Configuration > Add New > choose Maven 
      - Name: IC Core
      - Working directory: give the path of iccode-core
      - Command line: __clean install -DskipTests__ # Skip the test
      - Click Apply & ok then run it. No need VPN connection
      - __Since it uses the old version of jdk, an unexpected error has accured: __java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty__
        _Basically it claims that the cacerts file is empty. If you do not get this error do not do the following step_
         - So take the new nonempty cacerts file and put it here (location: \Users\.jdks\jdk8u172-b11\jre\lib\security).__
         - I took the cacert file of java-11-openjdk-11.0.12.7-1 from [Github](https://github.com/ojdkbuild/ojdkbuild)

    - Add a new target 
      - Name: IC API
      - Working directory: give the path of iccode-library-api
      - Command line: __clean install__  # Do not skip the test
      - Click Apply & ok then run it. No need VPN connection

    - Add a new target 
      - Name: IC LIB 
      - Working directory: give path of iccode-library
      - Command line: __clean install__  # Do not skip the test
      - Click Apply & ok then run it. No need VPN connection

    - Add a new target 
      - Name: IC API Javadoc
      - Working directory: give the path of iccode-library-api
      - Command line: __clean javadoc:jar install__
      - Click Apply & ok then run it. No need VPN connection
      - Extract it:( _change the file ic-code-library-api.2.0.2-javadoc.jar in Users\ic-code-library-api\target to ic-code-library-api.2.0.2-javadoc.zip and extract it_) 
       - There are some documentation about each class.

- Install VisualVM Launcher. _Since we want to test a use case which has been declared taking too much time, therefore it requires VisualVM profiler in order to profiling the code._ 
  - Download the jar file from [Plugins Jetbrains](https://plugins.jetbrains.com/plugin/7115-visualvm-launcher)
  - to install that go to Intelij > File > Setting > Plugin > choose install from disk > choose the jar file. 
  - Download the VisualVM 2.1.1 from [Github](https://visualvm.github.io/) & unzip the file.
  - Back to Intelij > File > Setting > VisualVM Launcher[Github](https://visualvm.github.io/download.html)
  - VisualVM executable: give the path of visualvm.exe (C:\visualvm_211\bin\visualvm.exe)
  - Custom JDK home path: "C:\Users\.jdks\jdk8u172-b11\bin"


## Usage

Test the use case schnittmenge_roh.txt as a Prcode.

## Project Status
Project is: _complete_ /_need some tests and improvements_.


## Room for Improvement

Room for improvement:
- Improvement to be done for use case schnittmenge_roh.txt #(This file consists of a prcode and need to be invoked as an input for iccodecalculator)


To do:
- Test some use cases and profiling them with VisualVM.



## Acknowledgements
- This project was requested by _Porsche AG_. 


## Contact
Created by [@fschmeding](extern.florian.schmeding@porsche.de).
