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
