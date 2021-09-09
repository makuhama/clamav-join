# clamav-join

Join clamav-rest and clamav-java into one repository.

We have two libraries (clamav-rest and clamav-java) that need to patched. Unfortunately
we are facing issues getting the patched version published so that we can reference them
within Maven build triggered by a Docker build.

The idea is to join the two affected git repositories into one by means of git submodules.
The OpenShift BuildConfig checks out clamav-join and pushes the sources into the build
container. The Docker build starts by copying the sources into the target container. Two
Maven builds are run by the Docker build - one for clamav-java and the other one for
java-rest.
