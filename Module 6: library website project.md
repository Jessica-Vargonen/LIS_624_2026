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

10. `sudo cp db.ini updated-db.ini` to copy the file that I will be editing

11. `sudo edit updated-db.ini` to input login inforamtion

12. 
