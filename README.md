# Helm Chart testing with TravisCI
This repository is for testing a [helm](https://www.helm.sh/) chart with [TravisCI](https://travis-ci.org/)

## Requirements
You must have a GitHub and TravisCI accounts. See [setup instructions](https://docs.travis-ci.com/user/getting-started/).

## High level
The two important parts of this repository are the `test.sh` script and `.travis.yml` file.
- `test.sh` - this has all the test flow as a shell script
- `.travis.yml` - this describes the test stages for travisCI

## Demo Helm Chart
The included helm chart is a default output of the `helm create demo` command that generates a simple nginx Helm CHart example.

## Running locally
You run the tests locally, you should be running on Linux only!

### Vagrant for local testing
If on a non Linux OS (like Windows or Mac OS), you can use [vagrant](https://www.vagrantup.com/) to spin up an Ubuntu Linux VM.
```bash
# Spin up the Ubuntu Linux VM
$ vagrant up

# SSH into the VM
$ vagrant ssh

# Go to directory with the sources
$ cd /vagrant_data
```

### Running the tests
Run the test by executing the `test.sh` script (as root or with sudo)
```bash
$ sudo ./test.sh
```

## TravisCI tests
The TravisCI test calls the `test.sh` script which
- Sets up `kubectl` and `helm`
- Runs a `helm lint` on the `demo` chart
- Starts a local minikube
- Deploys `demo` chart

## Thanks
This repository is using examples from
- https://github.com/LiliC/travis-minikube. Thanks [Lili Cosic](https://github.com/LiliC)!
- https://gist.github.com/mbn18/0d6ff5cb217c36419661 Thank [Michael Ben-Nes](https://gist.github.com/mbn18)
