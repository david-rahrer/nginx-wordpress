nginx-wordpress
===============

Nginx and PHP-FPM configuration for Wordpress install. Current work goes into "development" branch and is merged to master periodically. MySQL configs are designed for MariaDB on low resource VPS such as Digital Ocean $5 - $20 droplet. Some changes would be needed for more robust systems, mainly in my.cnf. Nginx and PHP should work as configured on wide range of systems.

To Do
=====

1. Split into major sections using *.conf includes.
