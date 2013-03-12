## Getting Started ##

First, install [VirtualBox](https://www.virtualbox.org/wiki/Downloads).

Grab vagrant, librarian, etc:

	bundle

Grab the cookbooks (defined in Cheffile):
	
	librarian-chef install

And boot:

	vagrant up
	
The 'Vagrantfile' runs the cookbooks to install mysql, fetch WordPress and install it, setup port forwarding and all of that.

## What's left to do ##

Get a database dump restored into your dev machine! You can grab one of the auto-dumps from S3 and do it from your dev machine because the mysql port is forwarded thru the VM. This way we don't have to put the S3 secret keys inside the VM or config files. But maybe there's an ENV variable way to automate the DB pull.