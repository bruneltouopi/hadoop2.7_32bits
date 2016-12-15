# hadoop2.7_32bits
This is a project to how to setup a hadoop 2.7 in ubuntu 14.04LTS

How compile Hadoop for 32 Bits on ubuntu

before start update your ubuntu

Part1:Setup the lib

>sudo apt-get update

1-Install GNU C compiler

>sudo apt-get install -y build-essential

>sudo apt-get install gcc

2-Install GNU Autools Chain: autoconf, automake, libtool

>sudo apt-get install libtool

>sudo apt-get install autoconf

>sudo apt-get install automake

3-install zlib-development package

>sudo apt-get install zlib1g-dev

4-install openssl-development package

>sudo apt-get install openssh-server

>sudo apt-get install libssl-dev
  
5-Install JDK example 1.8.111

Define JAVA_HOME variable env in /etc/bash.bashrc

export JAVA_HOME=/usr/local/jdk1.8.111

define the java alternatives

6-Install maven and define MAVEN_HOME in path

7-Build Hadoop Source

Connect in ssh

>localhost ssh

For my case Hadoop 2.7.2

>mvn package -Pdist,native -DskipTests -Dtar

During install there are some issues

***antun plugin 1.7 is not compatible or inaccessible ***

go in hadoop-src pom.xml and upgrade version from 1.7 to 1.8

<maven-antrun-plugin.version>1.8</maven-antrun-plugin.version>

***proto --version error***

Install protobuff

>wget https://github.com/google/protobuf/releases/download/v2.5.0/protobuf-2.5.0.tar.gz

>tar -xzf protobuf-2.5.0.tar.gz

>cd protobuf-2.5.0

>./configure

>make

>make check

>make install

>sudo ldconfig

>protoc --version

