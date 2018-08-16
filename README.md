# Jib Example

The simplest Docker implementation ever. No knowledge of Docker is necessary to build a Docker image and run it from the command line with the help of Jib.
Further documentation for Jib can be found here: https://github.com/GoogleContainerTools/jib.

To use:

* From the root directory, `cd example1/java-example`
* `./gradlew jibDockerBuild` to build locally
* `docker run -p 8080:8080 java-example:1.0.0-SNAPSHOT`

To build a docker image locally:

* From the root directory, `cd example1/java-example`
* `./gradlew jibExportDockerContext` to build the image
* From that directory, `cd build/jib-docker-context/libs` and then you can open up the new Dockerfile that's been generated.

To deploy a docker image to Docker Hub or Artifactory:

* In the build.gradle file include the following: 
```groovy
jib {
	from {
		image = 'openjdk:8-jdk-alpine'
	}
	to {
		image = '<if_not_docker_hub_include_root_url/docker_hub_or_artifactory_repo/image_name>'
		auth {
			username = "${username}"
			password = "${password}"
		}
	}
	container {
		jvmFlags = ['-Xms512m', '-Xdebug']
		mainClass = 'hello.Application'
	}
	allowInsecureRegistries=true
}
```
* From the root directory, `cd example1/java-example`
  * `./gradlew jib` to build and deploy the image to Docker Hub (or wherever your artifacts are stored)

