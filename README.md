Vagrant Configuration File for Deploying Docker on Ubuntu Raring Cloud EMI/AMI
========================

This repository contains the Vagrant configuration file for launching Docker on a Ubuntu Raring Cloud EMI/AMI.  It is intended to be used with the steps mentioned in the blog entry [Yet Another AWS Compatibility Example Using Vagrant-AWS Plugin and Eucalyptus 3.4 to Deploy Docker](http://blogs.mindspew-age.com/2014/02/16/yet-another-aws-compatibility-example-using-vagrant-aws-plugin-and-eucalyptus-3-4-to-deploy-docker/).  Below are the steps regarding how to use this file with Vagrant to deploy a Docker instance on Eucalyptus:

### Steps To Deploy Docker instance on Eucalyptus Using Vagrant

* Install Vagrant from [http://www.vagrantup.com/](http://www.vagrantup.com/). (optional – package manager can be used here instead)
* Install the [vagrant aws plugin](https://github.com/mitchellh/vagrant-aws): 
```
$ vagrant plugin install vagrant-aws
```
* Check out the Vagrantfile from this repository:
```
$ $ git clone https://github.com/hspencer77/eucalyptus-docker-raring.git
```
* Edit the following variables in the VagrantFile to match the user information for the Eucalyptus cloud that will run the Docker instance:
```
AWS_ENDPOINT = "<EC2_URL for Eucalyptus Cloud>"
AWS_AMI = "<ID for Ubuntu Raring EMI>"
AWS_ACCESS_KEY = "<Access Key ID>"
AWS_SECRET_KEY = "<Secret Key>"
AWS_KEYPAIR_NAME = "<Key Pair name>"
AWS_INSTANCE_TYPE = '<VM type>'
SSH_PRIVKEY_PATH = "<The path to the private key for the named keypair, for example ~/.ssh/docker.pem>"
```
* Run the following command to launch the instance:
```
$ vagrant up --provider=aws
```
* After the instance is launched, SSH into the instance using the following command:
```
$ vagrant ssh
```

Once you have SSH'ed into the instance, check out [the examples Docker provides in their documentation](https://docs.docker.io/en/latest/examples/hello_world/) for testing out the Docker deployment.

