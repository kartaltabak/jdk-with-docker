# jdk-with-docker

This repository provides JDK images with built-in docker support. 

## Release Notes: 

### 2025-11-10:

openjdk images are deprecated. We are migrating the images to `eclipse-temurin`. 
There are some side effects. Most notable one is the UID/GID conflict. 
We were creating `1000:1000` as a new user and assigning docker group to that user. 
However, on `eclipse-temurin`, there is already `1000:1000` assigned to `ubuntu`. 
Instead of creating a new user, we shall be reusing `ubuntu`.
That may break any usages of this image, if they are relying on the name of the `1000:1000` user. 

Moreover, specifically, openjdk's jdk21 is based on centos. 
`eclipse-temurin` is based on ubuntu. 
That may create additional migration issues if the usage of this image assumes CentOS and related tools, 
such as `microdnf`. 