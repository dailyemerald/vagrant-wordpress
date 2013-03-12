## Getting Started ##

If you haven't, install [VirtualBox](https://www.virtualbox.org/wiki/Downloads).

Then:

	bash init.sh

**OR** the hard way (this is the contents of the init.sh script):

	bundle	
	librarian-chef install
	vagrant up
	
- *bundle* pulls the gems. *knife-solo*, *librarian*, *vagrant* specifically. 
- *librarian-chef install* pulls the cookbooks from opscode. 
- *vagrant up* runs the recipes fetched by Librarian and boots the VM. It also sets some config stuff, like setting the **root mysql password to 'helloworld'**

### Connecting to ysql from the host machine ##

Is probably something like this:

	mysql --port=3306 --protocol=TCP -u root -h 127.0.0.1 -p

Restoring a DB backup might look like:

	mysql --port=3306 --protocol=TCP -u root -h 127.0.0.1 -p wordpress < db.sql

## What's left to do ##

- Auto-restore a database dump. We keep DB snapshots in S3, so this is probably a s3cmd command and some minor plumbing.

- Lots of other things.

