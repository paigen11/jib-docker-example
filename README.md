# Jib Example

The simplest Docker implementation ever. No knowledge of Docker is necessary to build a Docker image and run it from the command line with the help of Jib.
Further documentation for Jib can be found here: https://github.com/GoogleContainerTools/jib.

To use:

* `./gradlew jibDockerBuild' to build locally
* `./gradlew jib --image=java-example:1.0.0-SNAPSHOT` to build and deploy to Docker Hub

To run:

* `docker run -p 8080:8080 java-example:1.0.0-SNAPSHOT`