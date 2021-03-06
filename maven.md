# Maven
Maven is essentially a project management and comprehension tool and provides a way to help with managing 
*Builds
*Documentation
*Reporting
*Dependencies
*Releases
*SCMs
*Distribution

Maven accelerates development cycle while at the same time helps us achieve a higher rate of success.

## Setting up Maven
Maven Configuration occurs at 3 levels.
* Project - most static configuration occurs in pom.xml.
* Installation - this is configuration added once for a Maven installation.
* User -  this is configuration specific to a particular user.

## Configuring in Local Repository
The location of our local repository can be changed in user configuration. The default value is ${user.home}/.m2/repository/.
```<settings>
  ...
  <localRepository>/path/to/local/repo/</localRepository>
  ...
  </settings>
  ```

## Configuring Parallel Artifact Resolution
By default, Maven 2.1.0+ will download up to 5 artifacts (from different groups) at once.
To change the size of the thread pool, start Maven using -Dmaven.artifact.threads.

**mvn -Dmaven.artifact.threads=1 verify**
## Making first Maven Project
 * To create our first Maven project we are going to use Maven's archetype mechanism.
 * An archetype is defined as an original pattern or model from which all other things of the same kind are made.
 * In Maven, an archetype is a template of a project which is combined with some user input to produce a working Maven project that has been tailored to the user's requirements.
   ```mvn -B archetype:generate \
  -DarchetypeGroupId=org.apache.maven.archetypes \
  -DgroupId=com.mycompany.app \
  -DartifactId=my-app
  ```
 
## POM
 * POM stands for Project Object Model. The POM is the basic unit of work in Maven. 
 * In short, the POM contains every important piece of information about our project.
 
## Key elements of POM
* project - This is the top-level element in all Maven pom.xml files.
* modelVersion - This element indicates what version of the object model this POM is using.
* groupId - This element indicates the unique identifier of the organization or group that created the project.
* artifactId - This element indicates the unique base name of the primary artifact being generated by this project. The primary artifact for a project is typically a JAR file.
* packaging - This element indicates the package type to be used by this artifact (e.g. JAR, WAR, EAR, etc.). Default value is JAR.
* version - This element indicates the version of the artifact generated by the project.
* name - This indicates the name of the project.
* url - This element indicates where the project's site can be found. 
* description - This provides basic description of the project.

## Compiling Application Sources
Change to the directory where pom is created and execute the following.
           **mvn compile**
## Compiling Test Sources
To compile test sources execute the following command.
           **mvn test**
To compile test sources (but not execute the tests), execute the following:
           **mvn test-compile**
## Creating a JAR
To create a JAR, execute the following
          **mvn package**
To install the JAR to our local reposiroty, execute the following.
          **mvn install**
**mvn clean** - Remove target directory with all the build data before starting so that it is fresh.

## SNAPSHOT Version
* The SNAPSHOT value refers to the 'latest' code along a development branch, and provides no guarantee the code is stable. 
* Code in a release version is unchanging.
* It is the 'development' version before the final 'release' version. 

## Plugin
* Plugins are where much of the real action is performed. 
* Plugins are used to create jar files, create war files, compile code, unit test code, create project documentation, and on and on.
* One of the simplest plugins is clean which removes the target directory.

## External Dependencies
* The dependencies section of pom.xml will define all of the external dependencies required to build our project.
* For each external dependency, we need to define groupId, artifactId, version and scope. 
* Scope indicates how the project uses that dependency and may include compile, test and runtime.

## Creating Documentation
 
 **mvn archetype:generate \
  -DarchetypeGroupId=org.apache.maven.archetypes \
  -DarchetypeArtifactId=maven-archetype-site \
  -DgroupId=com.mycompany.app \
  -DartifactId=my-app-site**
