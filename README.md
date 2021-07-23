# Install script for yiimp on Ubuntu 18.04

Official Yiimp (used in this script for Yiimp Installation): https://github.com/tpruvot/yiimp
j
***********************************

USE THIS SCRIPT ON FRESH INSTALL UBUNTU!

Use only for tests on a local or virtual server! NOT TESTED IN PROD!

Be careful with the new Yiimp install scripts. Many of the wallets do not compile on Ubuntu above 16.04. There are workarounds, but you have to know how to do it to compile the wallets.

Connect on your VPS =>
- adduser pool (for example, change to your)
- adduser pool sudo
- su - pool
- sudo apt-get -y install git
- git clone https://github.com/xavatar/yiimp_install_scrypt_ubuntu18.04.git
- cd yiimp_install_scrypt_ubuntu18.04
- sudo bash install.sh (Do not run the script as root!)
- sudo usermod -a -G www-data pool
- sudo bash screen-scrypt.sh (Do not run the script as root!)
- nano screen-stratum.sh (CONFIGURE BEFORE START this script... add or remove algo you use)
- sudo bash screen-stratum.sh

Finish !
Go http://xxx.xxxxxx.xxx or https://xxx.xxxxxx.xxx (if you have chosen LetsEncrypt SSL). Enjoy !

!!! Don't forget to install and run daemons for your coins !!!!

###### :bangbang: **YOU MUST UPDATE THE FOLLOWING FILES :**
- **/var/web/serverconfig.php :** update this file to include your public ip (line = YAAMP_ADMIN_IP) to access the admin panel (Put your PERSONAL IP, NOT IP of your VPS). update with public keys from exchanges. update with other information specific to your server..
- **/etc/yiimp/keys.php :** update with secrect keys from the exchanges (not mandatory)


###### :bangbang: **IMPORTANT** : 

- The configuration of yiimp and coin require a minimum of knowledge in linux
- Your mysql information (login/Password) is saved in **~/.my.cnf**
- **If you reboot your VPS**, you must restart screen-scrypt.sh (or add crontab)
- Remember to restart **memcached service** after the db change (update or import new .sql)

***********************************

###### This script has an interactive beginning and will ask for the following information :

- Enter time zone
- Server Name 
- Are you using a subdomain
- Enter support email
- Set stratum to AutoExchange
- New location for /site/adminRights
- Your Public IP for admin access (Put your PERSONNAL IP, NOT IP of your VPS)
- Install Fail2ban (not mandatory for local server)
- Install UFW and configure ports (not mandatory for local server)
- Install LetsEncrypt SSL (not required for local server)

***********************************

**This install script will get you 95% ready to go with yiimp. There are a few things you need to do after the main install is finished.**

While I did add some server security to the script, it is every server owners responsibility to fully secure their own servers. After the installation you will still need to customize your serverconfig.php file to your liking, add your API keys, and build/add your coins to the control panel. 

There will be several wallets already in yiimp. These have nothing to do with the installation script and are from the database import from the yiimp github. 

