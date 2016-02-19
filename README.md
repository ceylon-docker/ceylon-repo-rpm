# Building a Ceylon YUM/DNF repository

The following images/tags are available:

 - `latest` ([ceylon-repo-rpm/Dockerfile](https://github.com/ceylon-docker/ceylon-repo-rpm/blob/master/Dockerfile))

To run the build perform the following steps:

 1. First make sure you have built the [Ceylon RPM package](https://hub.docker.com/r/ceylon/ceylon-package-rpm/)
 2. `docker pull ceylon/ceylon-repo-rpm:latest`
 3. `docker run -t --rm -v /tmp/ceylon:/output -v ~/.gnupg:/home/ceylon/.gnupg ceylon/ceylon-repo-rpm:latest`

The Docker image can't contain any sensitive information of course, so for the purpose of signing the packages you can point Docker to your own GnuPG key ring in your home or any other directory. That's the purpose of the `-v ~/.gnupg:/home/ceylon/.gnupg` volume.

If the build completed successfully the resulting YUM/DNF repository can be found in `/tmp/ceylon/repodata`.

NB: The `/tmp/ceylon` folder used in the example can be any folder but you *have* to use it's full path in the command and it must contain the result that was obtained by running the build for the  [Ceylon RPM package](https://hub.docker.com/r/ceylon/ceylon-package-rpm/) first!
