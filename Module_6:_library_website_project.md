# Install WordPress

### Steps

1. `sudo apt install php-curl php-xml php-imagick php-mbstring php-zip php-intl`

2. `cd /var/www/html`

3. `sudo wget https://wordpress.org/latest.zip`

4. `sudo apt install unzip`

5. `sudo unzip latest.zip`

6. `sudo rm latest.zip`: to remove file that is no longer needed

7. `sudo mysql -u root`

8. `create user 'insert username'@'localhost' identified by 'insert password';`

9. `create database wordpress;` to create a database called worpress

10. `grant all privileges on insert database name.* to 'insert username'@'localhost';`

11. `show databases;` to ensure the one created shows up

12. `cd wordpress/` to enter the wordpress directory

13. `sudo cp wp-config-sample.php wp-config.php` to copy sample file to config file

14. `sudo edit wp-config.php` put in information that we just created

15. `sudo mv /var/www/html/wordpress /var/www/html/library` to rename site from wordpress to library

16. Finish installing on website

### Reflection
- Installing wordpress went well. It was very straight forward.

# Installing Omeka

### Steps:

1. `sudo apt update; sudo apt upgrade -y; sudo apt autoremove -y; sudo apt clean` to update system

2. `program --version` ex: `mysql --version` to make sure that the systems I'm running will work with Omeka

3. `sudo apt install imagemagick` to install imagemagick

4. `sudo a2enmod rewrite` to rewrite URLs

5. `sudo systemctl restart apache2` to restart apache2

6. `sudo wget https://github.com/omeka/Omeka/releases/download/v3.2/omeka-3.2.zip` to download Omeka

7. `sudo unzip omeka-3.2.zip` to unzip omeka file

8. `cd /var/www/html/omeka` This didn't work because there isn't an omeka directory

9. `cd /var/www/html/omeka-3.2` to open the omeka directory

10. `sudo mv omeka-3.2 omeka` to move the directory to omeka

11. `sudo edit db.ini` to replace the 'XXX' values with my values

12. site didn't work

13. `sudo edit .htaccess` added in my directory

14. got a 404 error for site

### Reflection:

I was unable to solve the problem of why my site refused to work. Had a meeting with Dr. Burns and we still couldn't figure out the problem so we restarted. 

### Steps:

1. `sudo cp db.ini ~` to copy file to home directory

2. `sudo rm -rf diglib` to remove the file which we had changed the name of to see if that would help

3. `sudo unzip omeka-3.2.zip` to reinstall the file

4. `ls -l` to look at the directory

5. `sudo mv omeka-3.2 omeka` to change directory to omeka

6. `cd omeka` to open directory

7. `ls -l` to look at directory

8. `sudo cp ~/db.ini .` to copy the file

9. `sudo chmod -R g+w files/` to be able to change and modify the files

10. now it works!

# Installing Koha

### Steps:

1) create new virtual instance

2) input firewall rules

3) open new machine

4) `sudo apt update; sudo apt upgrade -y; sudo apt autoremove -y; sudo apt clean` to update machine

5) `tmux` in case I get disconnected while working I can go back to where I left off

6) `sudo apt install apt-transport-https ca-certificates curl` to setup signing keys

7) `sudo mkdir -p --mode=0755 /etc/apt/keyrings` to setup signing keys

8) `sudo curl -fsSL https://debian.koha-community.org/koha/gpg.asc -o /etc/apt/keyrings/koha.asc` to setup signing keys

9) `sudo su` to become the root user

10) `tee /etc/apt/sources.list.d/koha.sources <<EOF
Types: deb
URIs: https://debian.koha-community.org/koha/
Suites: 25.05
Components: main
Signed-By: /etc/apt/keyrings/koha.asc
EOF`

11) `cat /etc/apt/sources.list.d/koha.sources` to check that the information was put in correctly

12) `exit` to exit root user

13) update machine

14) `sudo apt install mariadb-server` to install MariaDB server

15) update machine

16) `apt show koha-common` to review Koha

17) `sudo apt install koha-common` to install Koha

18) `sudo cp /etc/koha/koha-sites.conf /etc/koha/koha-sites.conf.backup` to create a backup file

19) `wget https://github.com/microsoft/edit/releases/download/v1.2.1/edit-1.2.0-x86_64-linux-gnu.tar.zst
tar -xf  edit-1.2.0-x86_64-linux-gnu.tar.zst
sudo install -m 0755 edit /usr/local/bin/edit` to install edit

20) `sudo edit /etc/koha/koha-sites.conf` to open and edit file

21) input INTRAPORT="8080" OPACPORT="8081"

22) `sudo a2enmod rewrite cgi headers proxy_http` to allow modifications

23) `sudo systemctl restart apache2` to restart apache

24) `systemctl status apache2` to make sure apache2 is running

25) `sudo cp /etc/apache2/ports.conf /etc/apache2/ports.conf.backup` to create apache2 backup file

26) `sudo edit /etc/apache2/ports.conf` to open and edit file

27) input Listen 8080 Listen 8081

28) `sudo koha-create --create-db bibliolib` to create a library called bibliolib

29) `sudo systemctl restart apache2` to restart apache2

30) `sudo a2dissite 000-default` to turn off wed document root

31) `sudo a2enmod deflate` to turn on network compression

32) `sudo a2ensite bibliolib` to enable bibliolib library

33) `sudo systemctl reload apache2` to reload apache2

34) `sudo systemctl restart apache2` to restart apache2

35) `systemctl status apache2` to ensure it is active

36) `sudo koha-passwd bibliolib` to get user name and password
    
```
Username for bibliolib: koha_bibliolib
Password for bibliolib: %DW.%TPeIdbN8RNw
```

37) go to site 35.193.164.194:8080 to setup admin account 

38) go to site 35.193.164.194:8081

### Reflection:

- This install went very well. I only ran into a hicup when I tried to edit the file the first time. This only happened because I didn't install my text editor onto the new system yet. So this was a very simple fix. I just installed edit and moved on from there. I was able to create users and add books to my site. I might just use this for my home library since I have five bookshelves of books. 
