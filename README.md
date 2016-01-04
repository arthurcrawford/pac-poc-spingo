# pac-poc-spingo
Proof-of-concept to demonstrate a code repo with a requirement for implementing a standardised convention for project packaging, build & release lifecycle.

## Building the project

### Dependencies
* `/bin/sh`
* [`Docker`](https://www.docker.com/) 

### Very Quickly

	$ git clone git@github.com:arthurcrawford/pac-poc-spingo.git
	$ cd pac-poc-spingo
	$ ./build.sh deploy

For this to work, access privileges are required for the source and target repos.

### More detail

The above command did everything necessary to build, package, release and deploy packaged binaries.  In detail, the build script actually performs the following phases in order.

```sh
./build.sh clean
./build.sh compile
./build.sh test
./build.sh package
./build.sh install
./build.sh release
./build.sh deploy
```
You can execute the script at the desired intermediate phase. 
Each phase performs the proceeding ones.  

By default, the build script instantiates a Docker container, primed with the necessary dependencies, and runs the build/release tasks in this.  This implies  required access and permission to the necessary, federated Docker repo. 

If the advanced option `[--local, -l]` is specified, Docker will *not* be used and the script will, instead, assume all the necessary dependencies are already present in the local environment.

**clean**
Removes any previously generated build products.  

**compile**
Performs any required compilation phase.  

**test**
Unit tests code.  

**package**
Creates packages.  

**install**
Installs compiled packages to local repositories.  

**release**
Performs version management and VCS operations for tying VCS tags into package versions.  Requires commit privileges on the target VCS.

**deploy**
Copies packages to target repos.  Requires upload privilege on the target repos.

