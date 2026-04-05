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

16.    
