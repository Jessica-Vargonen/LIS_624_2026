# LIS_624_2026

## Managing Software

### Steps


`show databaes;`:
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+





1) `apt search tldr`: 

2) `sudo apt install tldr`: installed

3) `tldr grep`: directory does not exist 

4) `sudo apt --purge remove tldr`: removed tldr

5) `sudo apt autoremove`: removed tldr, freed up 27.8 MB disk space

6) `sudo apt clean`: to remove cached packages

7) `sudo apt install tldr-py`: installed

8) `tldr grep`: no such command 

9) `tldr -h`

10) `sudo apt --purge remove tldr-py`: removed, freed up 42 kB

11) `apt search bsd games`

## Installing the Apache Web Server

### Steps


1) `apt search apache2 | head`

2) `apt show apache2`

3) `cd /var/`: now in var directory 

4) `ls`: backups  cache  crash  lib  local  lock  log  mail  opt  run  snap  spool  tmp

5) `sudo apt install apache2`

6) `ls`: backups  cache  crash  lib  local  lock  log  mail  opt  run  snap  spool  tmp  www

7) `systemctl status apache2`: active

8) `sudo apt install elinks`

9) `elinks 127.0.0.1`: It works

10) `ip a`

11) `elinks http://10.128.0.3`: It works

12) `cd /www/html`: -bash: cd: /www/html: No such file or directory, I forgot to put
    /var in front

13) `cd /var/www/html/`: jessieloso@spring-2026-jvargo:/var/www/html$ 

14) `ls`: index.html

15) `sudo mv index.html index.orginal.html`

16) `ls`: index.original.html

17) `sudo edit index.html`: opens edit

`<html>
<head>
<title>My first web page using Apache</title>
</head>
<body>

<h1>Welcome</h1>

<p>Welcome to my web site.
I created this site using the Apache HTTP server.</p>

</body>
</html>`: when I refreshed page it said URL not found. I realized that I needed to save the
changes in edit then reload the page. When I refreshed it says Welcome

## Installing and Configuring PHP

### Steps

`apt show php`:
Package: php
Version: 2:8.3+93ubuntu2
Priority: optional
Section: php
Source: php-defaults (93ubuntu2)
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian PHP Maintainers <team+pkg-php@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 11.3 kB
Depends: php8.3
Download-Size: 4076 B
APT-Sources: http://us-central1.gce.archive.ubuntu.com/ubuntu noble/main amd64 Packages
Description: server-side, HTML-embedded scripting language (default)
 PHP (recursive acronym for PHP: Hypertext Preprocessor) is a widely-used
 open source general-purpose scripting language that is especially suited
 for web development and can be embedded into HTML.
 .
 This package is a dependency package, which depends on latest stable
 PHP version (currently 8.3).

`sudo apt install php libapache2-mod-php`:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libapache2-mod-php8.3 php-common php8.3 php8.3-cli php8.3-common php8.3-opcache php8.3-readline
Suggested packages:
  php-pear
The following NEW packages will be installed:
  libapache2-mod-php libapache2-mod-php8.3 php php-common php8.3 php8.3-cli php8.3-common php8.3-opcache
  php8.3-readline
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 4922 kB of archives.
After this operation, 22.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us-central1.gce.archive.ubuntu.com/ubuntu noble/main amd64 php-common all 2:93ubuntu2 [13.9 kB]
Get:2 http://us-central1.gce.archive.ubuntu.com/ubuntu noble-updates/main amd64 php8.3-common amd64 8.3.6-0ubuntu0.24.04.6 [740 kB]
Get:3 http://us-central1.gce.archive.ubuntu.com/ubuntu noble-updates/main amd64 php8.3-opcache amd64 8.3.6-0ubuntu0.24.04.6 [372 kB]
Get:4 http://us-central1.gce.archive.ubuntu.com/ubuntu noble-updates/main amd64 php8.3-readline amd64 8.3.6-0ubuntu0.24.04.6 [13.4 kB]
Get:5 http://us-central1.gce.archive.ubuntu.com/ubuntu noble-updates/main amd64 php8.3-cli amd64 8.3.6-0ubuntu0.24.04.6 [1916 kB]
Get:6 http://us-central1.gce.archive.ubuntu.com/ubuntu noble-updates/main amd64 libapache2-mod-php8.3 amd64 8.3.6-0ubuntu0.24.04.6 [1850 kB]
Get:7 http://us-central1.gce.archive.ubuntu.com/ubuntu noble/main amd64 libapache2-mod-php all 2:8.3+93ubuntu2 [4224 B]
Get:8 http://us-central1.gce.archive.ubuntu.com/ubuntu noble-updates/main amd64 php8.3 all 8.3.6-0ubuntu0.24.04.6 [9172 B]
Get:9 http://us-central1.gce.archive.ubuntu.com/ubuntu noble/main amd64 php all 2:8.3+93ubuntu2 [4076 B]
Fetched 4922 kB in 0s (11.5 MB/s)
Selecting previously unselected package php-common.
(Reading database ... 106753 files and directories currently installed.)
Preparing to unpack .../0-php-common_2%3a93ubuntu2_all.deb ...
Unpacking php-common (2:93ubuntu2) ...
Selecting previously unselected package php8.3-common.
Preparing to unpack .../1-php8.3-common_8.3.6-0ubuntu0.24.04.6_amd64.deb ...
Unpacking php8.3-common (8.3.6-0ubuntu0.24.04.6) ...
Selecting previously unselected package php8.3-opcache.
Preparing to unpack .../2-php8.3-opcache_8.3.6-0ubuntu0.24.04.6_amd64.deb ...
Unpacking php8.3-opcache (8.3.6-0ubuntu0.24.04.6) ...
Selecting previously unselected package php8.3-readline.
Preparing to unpack .../3-php8.3-readline_8.3.6-0ubuntu0.24.04.6_amd64.deb ...
Unpacking php8.3-readline (8.3.6-0ubuntu0.24.04.6) ...
Selecting previously unselected package php8.3-cli.
Preparing to unpack .../4-php8.3-cli_8.3.6-0ubuntu0.24.04.6_amd64.deb ...
Unpacking php8.3-cli (8.3.6-0ubuntu0.24.04.6) ...
Selecting previously unselected package libapache2-mod-php8.3.
Preparing to unpack .../5-libapache2-mod-php8.3_8.3.6-0ubuntu0.24.04.6_amd64.deb ...
Unpacking libapache2-mod-php8.3 (8.3.6-0ubuntu0.24.04.6) ...
Selecting previously unselected package libapache2-mod-php.
Preparing to unpack .../6-libapache2-mod-php_2%3a8.3+93ubuntu2_all.deb ...
Unpacking libapache2-mod-php (2:8.3+93ubuntu2) ...
Selecting previously unselected package php8.3.
Preparing to unpack .../7-php8.3_8.3.6-0ubuntu0.24.04.6_all.deb ...
Unpacking php8.3 (8.3.6-0ubuntu0.24.04.6) ...
Selecting previously unselected package php.
Preparing to unpack .../8-php_2%3a8.3+93ubuntu2_all.deb ...
Unpacking php (2:8.3+93ubuntu2) ...
Setting up php-common (2:93ubuntu2) ...
Created symlink /etc/systemd/system/timers.target.wants/phpsessionclean.timer → /usr/lib/systemd/system/phpsessionclean.timer.
Setting up php8.3-common (8.3.6-0ubuntu0.24.04.6) ...

Creating config file /etc/php/8.3/mods-available/calendar.ini with new version

Creating config file /etc/php/8.3/mods-available/ctype.ini with new version

Creating config file /etc/php/8.3/mods-available/exif.ini with new version

Creating config file /etc/php/8.3/mods-available/fileinfo.ini with new version

Creating config file /etc/php/8.3/mods-available/ffi.ini with new version

Creating config file /etc/php/8.3/mods-available/ftp.ini with new version

Creating config file /etc/php/8.3/mods-available/gettext.ini with new version

Creating config file /etc/php/8.3/mods-available/iconv.ini with new version

Creating config file /etc/php/8.3/mods-available/pdo.ini with new version

Creating config file /etc/php/8.3/mods-available/phar.ini with new version

Creating config file /etc/php/8.3/mods-available/posix.ini with new version

Creating config file /etc/php/8.3/mods-available/shmop.ini with new version

Creating config file /etc/php/8.3/mods-available/sockets.ini with new version

Creating config file /etc/php/8.3/mods-available/sysvmsg.ini with new version

Creating config file /etc/php/8.3/mods-available/sysvsem.ini with new version

Creating config file /etc/php/8.3/mods-available/sysvshm.ini with new version

Creating config file /etc/php/8.3/mods-available/tokenizer.ini with new version
Setting up php8.3-readline (8.3.6-0ubuntu0.24.04.6) ...

Creating config file /etc/php/8.3/mods-available/readline.ini with new version
Setting up php8.3-opcache (8.3.6-0ubuntu0.24.04.6) ...

Creating config file /etc/php/8.3/mods-available/opcache.ini with new version
Setting up php8.3-cli (8.3.6-0ubuntu0.24.04.6) ...
update-alternatives: using /usr/bin/php8.3 to provide /usr/bin/php (php) in auto mode
update-alternatives: using /usr/bin/phar8.3 to provide /usr/bin/phar (phar) in auto mode
update-alternatives: using /usr/bin/phar.phar8.3 to provide /usr/bin/phar.phar (phar.phar) in auto mode

Creating config file /etc/php/8.3/cli/php.ini with new version
Setting up libapache2-mod-php8.3 (8.3.6-0ubuntu0.24.04.6) ...

Creating config file /etc/php/8.3/apache2/php.ini with new version
Module mpm_event disabled.
Enabling module mpm_prefork.
apache2_switch_mpm Switch to prefork
apache2_invoke: Enable module php8.3
Setting up php8.3 (8.3.6-0ubuntu0.24.04.6) ...
Setting up libapache2-mod-php (2:8.3+93ubuntu2) ...
Setting up php (2:8.3+93ubuntu2) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for php8.3-cli (8.3.6-0ubuntu0.24.04.6) ...
Processing triggers for libapache2-mod-php8.3 (8.3.6-0ubuntu0.24.04.6) ...
Scanning processes...                                                                                                 
Scanning candidates...                                                                                                
Scanning linux images...                                                                                              

Pending kernel upgrade!
Running kernel version:
  6.14.0-1021-gcp
Diagnostics:
  The currently running kernel version is not the expected kernel version 6.17.0-1008-gcp.

Restarting the system to load the new kernel will not be handled automatically, so you should consider rebooting.

Restarting services...

Service restarts being deferred:
 /etc/needrestart/restart.d/dbus.service
 systemctl restart getty@tty1.service
 systemctl restart networkd-dispatcher.service
 systemctl restart serial-getty@ttyS0.service
 systemctl restart unattended-upgrades.service

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.

`sudo systemctl restart apache2`
`php -v`:
PHP 8.3.6 (cli) (built: Jan  7 2026 08:40:32) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.3.6, Copyright (c) Zend Technologies
    with Zend OPcache v8.3.6, Copyright (c), by Zend Technologies

`systemctl status apache2`:
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/apache2.service; enabled; preset: enabled)
     Active: active (running) since Sun 2026-03-08 14:32:55 UTC; 1min 34s ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 2344397 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCESS)
   Main PID: 2344400 (apache2)
      Tasks: 6 (limit: 1072)
     Memory: 10.7M (peak: 11.2M)
        CPU: 66ms
     CGroup: /system.slice/apache2.service
             ├─2344400 /usr/sbin/apache2 -k start
             ├─2344402 /usr/sbin/apache2 -k start
             ├─2344403 /usr/sbin/apache2 -k start
             ├─2344404 /usr/sbin/apache2 -k start
             ├─2344405 /usr/sbin/apache2 -k start
             └─2344406 /usr/sbin/apache2 -k start

Mar 08 14:32:55 spring-2026-jvargo.us-central1-a.c.syslib-624-jvargonen.internal systemd[1]: Starting apache2.service>
Mar 08 14:32:55 spring-2026-jvargo.us-central1-a.c.syslib-624-jvargonen.internal systemd[1]: Started apache2.service >
lines 1-19/19 (END)

`cd /var/www/html/`: jessieloso@spring-2026-jvargo:/var/www/html$

`ls`: index.html  index.original.html

`sudo edit info.php`: open edit

`<?php
phpinfo();
?>`: PHP Version 8.3.6

`sudo rm /var/www/html/info.php`: removes file

`cd /etc/apache2/mods-available/`: jessieloso@spring-2026-jvargo:/etc/apache2/mods-available$

`ls`: list of mods available

`sudo cp dir.conf dir.conf.bak`: added backup

`sudo eidt dir.conf`: opens directory index in edit
insert index.php at the front and remove later listing.

`apachectl configtest`: syntax OK

`sudo systemctl reload apache2`: reloads system

`systemctl status apache2` :
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/apache2.service; enabled; preset: enabled)
     Active: active (running) since Sun 2026-03-08 14:32:55 UTC; 32min ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 2344397 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCESS)
    Process: 2346353 ExecReload=/usr/sbin/apachectl graceful (code=exited, status=0/SUCCESS)
   Main PID: 2344400 (apache2)
      Tasks: 6 (limit: 1072)
     Memory: 12.1M (peak: 29.9M)
        CPU: 401ms
     CGroup: /system.slice/apache2.service
             ├─2344400 /usr/sbin/apache2 -k start
             ├─2346358 /usr/sbin/apache2 -k start
             ├─2346359 /usr/sbin/apache2 -k start
             ├─2346360 /usr/sbin/apache2 -k start
             ├─2346361 /usr/sbin/apache2 -k start
             └─2346362 /usr/sbin/apache2 -k start

Mar 08 14:32:55 spring-2026-jvargo.us-central1-a.c.syslib-624-jvargonen.internal systemd[1]: Starting apache2.service>
Mar 08 14:32:55 spring-2026-jvargo.us-central1-a.c.syslib-624-jvargonen.internal systemd[1]: Started apache2.service >
Mar 08 15:04:47 spring-2026-jvargo.us-central1-a.c.syslib-624-jvargonen.internal systemd[1]: Reloading apache2.servic>
Mar 08 15:04:47 spring-2026-jvargo.us-central1-a.c.syslib-624-jvargonen.internal systemd[1]: Reloaded apache2.service>
lines 1-22/22 (END)

`cd /var/www/html/`: goes to the document root

`ls`: index.html  index.original.html

`sudo edit index.php`: File opened insert:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Browser Detector</title>
</head>
<body>
    <h1>Browser & OS Detection</h1>
    <p>You are using the following browser to view this site:</p>

    <?php
    $user_agent = $_SERVER['HTTP_USER_AGENT'];

    // Browser Detection
    if (stripos($user_agent, 'Edg') !== false || stripos($user_agent, 'Edge') !== false) {
        $browser = 'Microsoft Edge';
    } elseif (stripos($user_agent, 'Firefox') !== false) {
        $browser = 'Mozilla Firefox';
    } elseif (stripos($user_agent, 'Chrome') !== false && stripos($user_agent, 'Chromium') === false) {
        $browser = 'Google Chrome';
    } elseif (stripos($user_agent, 'Chromium') !== false) {
        $browser = 'Chromium';
    } elseif (stripos($user_agent, 'Opera Mini') !== false) {
        $browser = 'Opera Mini';
    } elseif (stripos($user_agent, 'Opera') !== false || stripos($user_agent, 'OPR') !== false) {
        $browser = 'Opera';
    } elseif (stripos($user_agent, 'Safari') !== false && stripos($user_agent, 'Chrome') === false) {
        $browser = 'Safari';
    } else {
        $browser = 'Unknown Browser';
    }

    // OS Detection
    if (stripos($user_agent, 'Windows') !== false) {
        $os = 'Windows';
    } elseif (stripos($user_agent, 'iOS') !== false || stripos($user_agent, 'iPhone') !== false || stripos($user_agent, 'iPad') !== false) {
        $os = 'iOS';
    } elseif (stripos($user_agent, 'Android') !== false) {
        $os = 'Android';
    } elseif (stripos($user_agent, 'Mac') !== false || stripos($user_agent, 'Macintosh') !== false) {
        $os = 'Mac';
    } elseif (stripos($user_agent, 'Linux') !== false) {
        $os = 'Linux';
    } else {
        $os = 'Unknown OS';
    }

    // Output Result
    echo "<p>Your browser is <strong>$browser</strong> and your operating system is <strong>$os</strong>.</p>";
    ?>

</body>
</html>

on web browser detected 

## Installing and Configuring MySQL

### Steps
`sudo apt update` : 
Hit:1 https://packages.cloud.google.com/apt google-cloud-ops-agent-noble-2 InRelease
Hit:2 http://us-central1.gce.archive.ubuntu.com/ubuntu noble InRelease                                               
Hit:3 http://us-central1.gce.archive.ubuntu.com/ubuntu noble-updates InRelease              
Hit:4 http://us-central1.gce.archive.ubuntu.com/ubuntu noble-backports InRelease
Hit:5 http://security.ubuntu.com/ubuntu noble-security InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
8 packages can be upgraded. Run 'apt list --upgradable' to see them.

`sudo upgrade`: sudo: upgrade: command not found
Forgot to put in apt

`sudo apt upgrage`:
Processing triggers for libc-bin (2.39-0ubuntu8.7) ...
Scanning processes...                                                                                                 
Scanning candidates...                                                                                                
Scanning linux images...                                                                                              

Pending kernel upgrade!
Running kernel version:
  6.14.0-1021-gcp
Diagnostics:
  The currently running kernel version is not the expected kernel version 6.17.0-1008-gcp.

Restarting the system to load the new kernel will not be handled automatically, so you should consider rebooting.

Restarting services...

Service restarts being deferred:
 /etc/needrestart/restart.d/dbus.service
 systemctl restart getty@tty1.service
 systemctl restart networkd-dispatcher.service
 systemctl restart serial-getty@ttyS0.service
 systemctl restart unattended-upgrades.service

No containers need to be restarted.

User sessions running outdated binaries:
 jessieloso @ user manager service: systemd[2146711]

No VM guests are running outdated hypervisor (qemu) binaries on this host.

`sudo apt autoremove`:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

`sudo apt clean`

`sudo apt install mysql-server`: installed

`apt policy mysql-server`: mysql-server:
  Installed: 8.0.45-0ubuntu0.24.04.1
  Candidate: 8.0.45-0ubuntu0.24.04.1
  Version table:
 *** 8.0.45-0ubuntu0.24.04.1 500
        500 http://us-central1.gce.archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages
        100 /var/lib/dpkg/status
     8.0.36-2ubuntu3 500
        500 http://us-central1.gce.archive.ubuntu.com/ubuntu noble/main amd64 Packages
   
`mysql --version`:
mysql  Ver 8.0.45-0ubuntu0.24.04.1 for Linux on x86_64 ((Ubuntu))

`systemctl status mysql`: 
● mysql.service - MySQL Community Server
     Loaded: loaded (/usr/lib/systemd/system/mysql.service; enabled; preset: enabled)
     Active: active (running) since Fri 2026-03-13 15:06:10 UTC; 4min 20s ago
    Process: 2682735 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
   Main PID: 2682744 (mysqld)
     Status: "Server is operational"
      Tasks: 37 (limit: 1072)
     Memory: 355.2M (peak: 366.2M)
        CPU: 4.123s
     CGroup: /system.slice/mysql.service
             └─2682744 /usr/sbin/mysqld

Mar 13 15:06:09 spring-2026-jvargo.us-central1-a.c.syslib-624-jvargonen.internal systemd[1]: Starting mysql.service ->
Mar 13 15:06:10 spring-2026-jvargo.us-central1-a.c.syslib-624-jvargonen.internal systemd[1]: Started mysql.service - >
lines 1-14/14 (END)

`sudo mysql_secure_installation`:
Securing the MySQL server deployment.

Connecting to MySQL using a blank password.

VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No: y

There are three levels of password validation policy:

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary                  file

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 0

Skipping password set for root as authentication with auth_socket is used by default.
If you would like to use password authentication instead, this can be done with the "ALTER_USER" command.
See https://dev.mysql.com/doc/refman/8.0/en/alter-user.html#alter-user-password-management for more information.

By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No) : y
Success.


Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No) : y
Success.

By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.


Remove test database and access to it? (Press y|Y for Yes, any other key for No) : y
 - Dropping test database...
Success.

 - Removing privileges on test database...
Success.

Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No) : y
Success.

All done! 

`sudo mysql -u root`:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 8.0.45-0ubuntu0.24.04.1 (Ubuntu)

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

`show databaes;`:
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.02 sec)

`\q`:
Bye

`sudo mysql -u root`

`create user 'opacuser'@'localhost' identified by 'XXXXXXXXX';`: 
Query OK, 0 rows affected (0.03 sec)

`create database opacdb default character set utf8mb4 collate utf8mb4_0900_ai_ci;`:
Query OK, 1 row affected (0.14 sec) 

`show databases;`: 
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| opacdb             |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.03 sec)

`grant all privileges on opacdb.* to 'opacuser'@'localhost';`:
Query OK, 0 rows affected (0.01 sec)

`edit ~/.bashrc`: open edit and on end add export mysql_ps1="[\d]> "

`source ~/.bashrc`

`mysql -u opacuser -p`: to sign in 

`show databases;`:
+--------------------+
| Database           |
+--------------------+
| information_schema |
| opacdb             |
| performance_schema |
+--------------------+
3 rows in set (0.06 sec)

`use opacdb;`:
Database changed

`create table books (
        id int unsigned not null auto_increment,
        author varchar(150) not null,
        title varchar(150) not null,
        copyright year not null,
        primary key (id)
);`:
Query OK, 0 rows affected (0.12 sec)

`show tables;`:
+------------------+
| Tables_in_opacdb |
+------------------+
| books            |
+------------------+
1 row in set (0.01 sec)

`describe books;`:
+-----------+--------------+------+-----+---------+----------------+
| Field     | Type         | Null | Key | Default | Extra          |
+-----------+--------------+------+-----+---------+----------------+
| id        | int unsigned | NO   | PRI | NULL    | auto_increment |
| author    | varchar(150) | NO   |     | NULL    |                |
| title     | varchar(150) | NO   |     | NULL    |                |
| copyright | year         | NO   |     | NULL    |                |
+-----------+--------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)

`insert into books (author, title, copyright) values
('Jennifer Egan', 'The Candy House', '2022'),
('Imbolo Mbue', 'How Beautiful We Were', '2021'),
('Lydia Millet', 'A Children\'s Bible', '2020'),
('Julia Phillips', 'Disappearing Earth', '2019');`:
Query OK, 4 rows affected (0.07 sec)
Records: 4  Duplicates: 0  Warnings: 0

`select * from books;`:
+----+----------------+-----------------------+-----------+
| id | author         | title                 | copyright |
+----+----------------+-----------------------+-----------+
|  1 | Jennifer Egan  | The Candy House       |      2022 |
|  2 | Imbolo Mbue    | How Beautiful We Were |      2021 |
|  3 | Lydia Millet   | A Children's Bible    |      2020 |
|  4 | Julia Phillips | Disappearing Earth    |      2019 |
+----+----------------+-----------------------+-----------+
4 rows in set (0.00 sec)

`select author from books;`:
+----------------+
| author         |
+----------------+
| Jennifer Egan  |
| Imbolo Mbue    |
| Lydia Millet   |
| Julia Phillips |
+----------------+
4 rows in set (0.00 sec)

`select copyright from books;`:
+-----------+
| copyright |
+-----------+
|      2022 |
|      2021 |
|      2020 |
|      2019 |
+-----------+
4 rows in set (0.00 sec)

`select author, title from books;`:
+----------------+-----------------------+
| author         | title                 |
+----------------+-----------------------+
| Jennifer Egan  | The Candy House       |
| Imbolo Mbue    | How Beautiful We Were |
| Lydia Millet   | A Children's Bible    |
| Julia Phillips | Disappearing Earth    |
+----------------+-----------------------+
4 rows in set (0.00 sec)

`select author from books where author like '%millet%';`:
+--------------+
| author       |
+--------------+
| Lydia Millet |
+--------------+
1 row in set (0.01 sec)

`select title from books where author like '%mbue%';`:
+-----------------------+
| title                 |
+-----------------------+
| How Beautiful We Were |
+-----------------------+
1 row in set (0.00 sec)

`select author, title form books where title not like '%e%';`:
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'books where title not like '%e%'' at line 1
I put form instead of from

`select author, title from books where title not like '%e%';':
Empty set (0.00 sec)
I need to remove the extra % after e

`select author, title from books where title not like '%e';'
+----------------+--------------------+
| author         | title              |
+----------------+--------------------+
| Julia Phillips | Disappearing Earth |
+----------------+--------------------+
1 row in set (0.00 sec)

`select * from books;`:
+----+----------------+-----------------------+-----------+
| id | author         | title                 | copyright |
+----+----------------+-----------------------+-----------+
|  1 | Jennifer Egan  | The Candy House       |      2022 |
|  2 | Imbolo Mbue    | How Beautiful We Were |      2021 |
|  3 | Lydia Millet   | A Children's Bible    |      2020 |
|  4 | Julia Phillips | Disappearing Earth    |      2019 |
+----+----------------+-----------------------+-----------+
4 rows in set (0.03 sec)

`alter table books add publisher varchar(75) after title;`:
Query OK, 0 rows affected (0.12 sec)
Records: 0  Duplicates: 0  Warnings: 0

`describe books;`:
+-----------+--------------+------+-----+---------+----------------+
| Field     | Type         | Null | Key | Default | Extra          |
+-----------+--------------+------+-----+---------+----------------+
| id        | int unsigned | NO   | PRI | NULL    | auto_increment |
| author    | varchar(150) | NO   |     | NULL    |                |
| title     | varchar(150) | NO   |     | NULL    |                |
| publisher | varchar(75)  | YES  |     | NULL    |                |
| copyright | year         | NO   |     | NULL    |                |
+-----------+--------------+------+-----+---------+----------------+
5 rows in set (0.02 sec)

`update books set publisher='Simon & Schuster' where id='1';`:
 Query OK, 1 row affected (0.08 sec)
Rows matched: 1  Changed: 1  Warnings: 0

`update books set publisher='Penguin Random House' where id='2';`:
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

`update books set publisher='W. W. Norton & Company' where id='3';`:
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

`update books set publisher='Knopf' where id='4';`:
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

`select * from books;`:
+----+----------------+-----------------------+------------------------+-----------+
| id | author         | title                 | publisher              | copyright |
+----+----------------+-----------------------+------------------------+-----------+
|  1 | Jennifer Egan  | The Candy House       | Simon & Schuster       |      2022 |
|  2 | Imbolo Mbue    | How Beautiful We Were | Penguin Random House   |      2021 |
|  3 | Lydia Millet   | A Children's Bible    | W. W. Norton & Company |      2020 |
|  4 | Julia Phillips | Disappearing Earth    | Knopf                  |      2019 |
+----+----------------+-----------------------+------------------------+-----------+
4 rows in set (0.01 sec)

`delete from books where author='Julia Phillips';`:
Query OK, 1 row affected (0.08 sec)

`insert into books
(author, title, publisher, copyright) values
('Chris Harris', 'My Head Has A Bellyache And More Nonsense', 'Little, Brown And Company', '2023'),
('Emily Winfield Martin', 'The Wonderful Things You Will Be', 'Random House', '2015'),
('Dav Pilkey', 'Dog Man Big Jim Believes', 'Scholastic Inc.', '2025');
I got an error, not sure why so I tried to add one book to see if it would work

`insert into books (author, title, publisher, copyright) values ('Chris Harris', 'My Head Has A Bellyache And More Nonsense', 'Little, Brown And Cpmpany', '2023');`:
Query OK, 1 row affected (0.03 sec)
This worked not sure what happened.

insert into books (author, title, publisher, copyright) values
    -> ('Emily Winfield Martin', 'The Wonderful Things You Will Be', 'Random House', '2025'),
    -> ('Dav Pilkey', 'Dog Man Big Jim Believes', 'Scholastic Inc.', '2025');
Query OK, 2 rows affected (0.02 sec)
Records: 2  Duplicates: 0  Warnings: 0
I was able to add two books at once so I'm not sure why the first one didn't work.

`select * from books;`:
+----+-----------------------+-------------------------------------------+---------------------------+-----------+
| id | author                | title                                     | publisher                 | copyright |
+----+-----------------------+-------------------------------------------+---------------------------+-----------+
|  1 | Jennifer Egan         | The Candy House                           | Simon & Schuster          |      2022 |
|  2 | Imbolo Mbue           | How Beautiful We Were                     | Penguin Random House      |      2021 |
|  3 | Lydia Millet          | A Children's Bible                        | W. W. Norton & Company    |      2020 |
|  5 | Chris Harris          | My Head Has A Bellyache And More Nonsense | Little, Brown And Cpmpany |      2023 |
|  6 | Emily Winfield Martin | The Wonderful Things You Will Be          | Random House              |      2025 |
|  7 | Dav Pilkey            | Dog Man Big Jim Believes                  | Scholastic Inc.           |      2025 |
+----+-----------------------+-------------------------------------------+---------------------------+-----------+
6 rows in set (0.03 sec)

`sudo apt install php-mysql`

`sudo systemctl restart apache2`
`sudo systemctl restart mysql`
`cd /var/www`
`sudo touch login.php`
`sudo chmod 640 login.php`
`ls -l login.php`:
-rw-r----- 1 root root 0 Mar 13 19:06 login.php

`sudo chown :www-data login.php`

`ls -l`: 
total 8
drwxr-xr-x 2 root root     4096 Mar  8 15:10 html
-rw-r----- 1 root www-data  134 Mar 15 14:09 login.php

`sudo edit login.php`: open edit add 
<?php // login.php
$db_hostname = "localhost";
$db_database = "opacdb";
$db_username = "opacuser";
$db_password = "XXXXXXXXX";
?>

`cd /var/www/html`

`sudo edit opac.php`: open edit add
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MySQL Server Example</title>
</head>
<body>

    <h1>A Basic OPAC</h1>
    <p>We can retrieve all the data from our database and book table using a couple of different queries.</p>

    <?php
    // Load MySQL credentials securely
    require_once '/var/www/login.php';

    // Enable detailed MySQL error reporting
    mysqli_report(MYSQLI_REPORT_ERROR | MYSQLI_REPORT_STRICT);

    // Establish database connection
    $conn = new mysqli($db_hostname, $db_username, $db_password, $db_database);

    if ($conn->connect_error) {
        die("Connection failed: " . $conn->connect_error);
    }

    echo "<h2>Query 1: Retrieving Publisher and Author Data</h2>";

    // Query using prepared statement
    $stmt = $conn->prepare("SELECT publisher, author FROM books");
    $stmt->execute();
    $result = $stmt->get_result();

    while ($row = $result->fetch_assoc()) {
        echo "<p>Publisher " . htmlspecialchars($row["publisher"]) .
             " published a book by " . htmlspecialchars($row["author"]) . ".</p>";
    }

    $stmt->close();

    echo "<h2>Query 2: Retrieving Author, Title, and Date Published Data</h2>";

    $stmt2 = $conn->prepare("SELECT author, title, copyright FROM books");
    $stmt2->execute();
    $result2 = $stmt2->get_result();

    while ($row = $result2->fetch_assoc()) {
        echo "<p>A book by " . htmlspecialchars($row["author"]) .
             " titled <em>" . htmlspecialchars($row["title"]) .
             "</em> was released in " . htmlspecialchars($row["copyright"]) . ".</p>";
    }

    $stmt2->close();
    $conn->close();
    ?>

</body>
</html>

`sudo php -f /var/www/login.php`: no output

`sudo php -f var/www/html/opac.php`: error couldn't open file opac.php
took a while to figure our that I forgot a / in front of var

`sudo php -f /var/www/html/opac.php`:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MySQL Server Example</title>
</head>
<body>

    <h1>A Basic OPAC</h1>
    <p>We can retrieve all the data from our database and book table using a couple of different queries.</p>

    <h2>Query 1: Retrieving Publisher and Author Data</h2><p>Publisher Simon &amp; Schuster published a book by Jennifer Egan.</p><p>Publisher Penguin Random House published a book by Imbolo Mbue.</p><p>Publisher W. W. Norton &amp; Company published a book by Lydia Millet.</p><p>Publisher Little, Brown And Cpmpany published a book by Chris Harris.</p><p>Publisher Random House published a book by Emily Winfield Martin.</p><p>Publisher Scholastic Inc. published a book by Dav Pilkey.</p><h2>Query 2: Retrieving Author, Title, and Date Published Data</h2><p>A book by Jennifer Egan titled <em>The Candy House</em> was released in 2022.</p><p>A book by Imbolo Mbue titled <em>How Beautiful We Were</em> was released in 2021.</p><p>A book by Lydia Millet titled <em>A Children&#039;s Bible</em> was released in 2020.</p><p>A book by Chris Harris titled <em>My Head Has A Bellyache And More Nonsense</em> was released in 2023.</p><p>A book by Emily Winfield Martin titled <em>The Wonderful Things You Will Be</em> was released in 2025.</p><p>A book by Dav Pilkey titled <em>Dog Man Big Jim Believes</em> was released in 2025.</p>
</body>
</html>

`cat ../login.php`:
cat: ../login.php: Permission denied

`sudo cat ../login.php`:
<?php // login.php
$db_hostname = "localhost";
$db_database = "opacdb";
$db_username = "opacuser";
$db_password = "XXXXXXXXXXX";

### Issues Encountered:

- `sudo upgrade`: sudo: upgrade: command not found
I forgot to put in apt 

- `select author, title from books where title not like '%e%';`: Empty set 
I need to remove the extra % after e

- `insert into books
(author, title, publisher, copyright) values
('Chris Harris', 'My Head Has A Bellyache And More Nonsense', 'Little, Brown And Company', '2023'),
('Emily Winfield Martin', 'The Wonderful Things You Will Be', 'Random House', '2015'),
('Dav Pilkey', 'Dog Man Big Jim Believes', 'Scholastic Inc.', '2025');`
I got an error, not sure why so I tried to add one book to see if it would work.
Adding one book worked. So I tried again with two books and it worked so I'm not sure why
my first command didn't work.

- `sudo php -f var/www/html/opac.php`: error couldn't open file opac.php
took a while to figure our that I forgot a / in front of var

### What I learned:

It is very important to ensure that everything is typed correctly. I am still not sure what
happended when I tried to add multiple books the first time. I learned how to install MySQL. 
I created a table and was able to search it for information. I also added to the table. I was 
able to pull specific data to my website.  
