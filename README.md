nginx-wordpress
===============

Nginx and PHP-FPM configuration for Wordpress install. Current work goes into "development" branch and is merged to master periodically. MySQL configs are designed for MariaDB on low resource VPS such as Digital Ocean $5 - $20 droplet. Some changes would be needed for more robust systems, mainly in my.cnf. Nginx and PHP should work as configured on wide range of systems.

Server Setup
============

The configuration files here are designed with Ubuntu and some specific package sources in mind. For Nginx I use the ppa from rtcamp at https://launchpad.net/~rtcamp/+archive/ubuntu/nginx.  This is built with the module to enable intelligent purging of the Nginx page cache - an excellent, lightweight alternative to the various plugins. It does reqire the use of the Nginx Helper plugin (from rtcamp as well) to be installed in Wordpress to take full advantage and to work best with Nginx in general.  This can be found at https://wordpress.org/plugins/nginx-helper/ and will also add a manual purge option to the admin.

For PHP I use the ppa at https://launchpad.net/~ondrej/+archive/ubuntu/php5 to keep up with the latest stable version. This is probably optional and the default Ubuntu source could be used fine.

For mysql I use MariaDB 10.x branch with great success. The source is https://downloads.mariadb.org/mariadb/repositories/#mirror=jmu&distro=Ubuntu and while regular mysql could probably be used without much trouble, you may need to tweak the my.cnf here and there. MariaDB is pretty much a dropin replacement, in this case for the mysql 5.6x line but I may have taken advantage of a MariaDB option that I forgot about.

In all these cases, if you use the altnerative sources, you should set up the appropriate apt preference files to keep the default versions from possibly installing over the preferred ones if the versions get mixed up and the default appears to supercede the installed ones. How to do that is explained here https://help.ubuntu.com/community/PinningHowto. My files are listed below as a reference.

https://gist.github.com/david-rahrer/084308227567a0355660

Permissions
===========

I'm not going into this in much detail but since others seem to be using these configs, I also wanted to explain that I create separate permissions for each site (as seen in the php pool files). I use the default www-data as the group and the individual user as the owner. This works well with chrooting in order to allow proper restricted access to users through SFTP to avoid the less secure FTP which I no longer install.

That should be enough to allow anyone to use these configs as a starting point. I've tried to incorporate all the current, reasonable security options and those elements necessary to make Nginx work with WP. If you have any suggestions, let me know.

To Do
=====

1. Split into major sections using *.conf includes.
