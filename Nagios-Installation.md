********************* 1. System Update and Dependencies Installation ***************************

$ sudo apt update
update ubuntu

$ sudo apt install -y wget build-essential libgd-dev libssl-dev apache2 php libapache2-mod-php perl
  
  Important libraries for Apache web server, PHP, C compiler and Nagios.

Step 2: Create User and Group for Nagios 
        sudo useradd nagios
        sudo groupadd nagcmd
        sudo usermod -a -G nagcmd nagios
        sudo usermod -a -G nagcmd www-data

Step 3: Nagios core download and compile
        cd /tmp
        wget -O nagioscore.tar.gz https://github.com/NagiosEnterprises/nagioscore/archive/refs/tags/nagios-4.4.6.tar.gz
        tar -xzf nagioscore.tar.gz
        cd nagioscore-nagios-4.4.6
        Nagios  source code tarball download and extract /tmp folder .

       ./configure --with-httpd-conf=/etc/apache2/sites-enabled

       It checks the system environment, configures the installation, and sets the Apache web server's configuration directory.

       $ make all
       Source code  binary files and cgi scripts  compile

       sudo make install
       sudo make install-init
       sudo make install-config
       sudo make install-commandmode
       sudo make install-webconf

 Main program, init scripts, sample configuration files, external command permissions, and Apache web configuration are installed in the system.

4. Web Interface & Apache Setup

      $sudo a2enmod rewrite cgi
      $sudo systemctl restart apache2

5. Firewall Integration & Configuration Commands

   $ sudo nano /usr/local/nagios/etc/hosts.cfg
It opens or creates a custom host configuration file to define details for new network devices, such as firewalls.

   $ sudo nano /usr/local/nagios/etc/nagios.cfg
I  open the Nagios configuration file, in which the path to the custom host file `cfg_file` is linked

   $sudo /usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg
It runs a pre-flight check to verify that there are no syntax errors or issues in the configuration files.

   $sudo systemctl restart nagios
    Restart the Nagios
