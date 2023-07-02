##  Install & configure Maven build tool on Jenkins
Maven is a code build tool which used to convert your code to an artifact. this is a widely used plugin to build in continuous integration

#### Prerequisites
1. Jenkins server

#### Install Maven on Jenkins:
1. To download the maven packages https://maven.apache.org/download.cgi on jenkins server.
 ## Creating maven directory under /opt
  mkdir /opt/maven
  cd /opt/maven

## downloading maven version 3.9.3:
  wget https://dlcdn.apache.org/maven/maven-3/3.9.3/binaries/apache-maven-3.9.3-bin.tar.gz

## Start extract the package using tar-xvzf:
  tar -xvzf apache-maven-3.9.3-bin.tar.gz

## Setup M2_HOME and M2 paths in .bash_profile of the user and add these to the path variable:
vi ~/.bash_profile

M2_HOME=/opt/maven

M2=/opt/maven/apache-maven-3.9.2/bin

JAVA_HOME=/usr/lib/jvm/java-17-amazon-corretto.x86_64/bin/java

PATH =$PATH:$HOME/bin:$JAVA:$M2_HOME:$M2

#### Checkpoint:
## update path:
echo $PATH

source .bash_profile #fetch the latest path

echo $PATH

## Start check the maven version on the root itself:
mvn --version

So far we have completed the installation of maven software to support maven plugin on the jenkins console. Let's jump onto Jenkins to complete the remaining steps

### Setup maven on Jenkins console:
1. Install maven plugin without restart  
  - `Manage Jenkins` > `Jenkins Plugins` > `available` > `Maven Invoker`
  - `Manage Jenkins` > `Jenkins Plugins` > `available` > `Maven Integration`

2. Configure maven path
  - `Manage Jenkins` > `Global Tool Configuration` > `Maven`
3. Start deploying the maven on jenkins by creating the first job.

4. Specify the goals that required for maven to install and deploy in it here we set the goals for maven is 'clean install' so that if anything there in package mean it will clean it completely and start installing the updated packages.
