********************************************** Step-by-Step Implementation Guide *****************************************

Step 1: Install Nagios Core Prerequisites

Update the Ubuntu system and install essential packages Apache, PHP, build utilities.

sudo apt update
sudo apt install -y wget build-essential libgd-dev libssl-dev apache2 php libapache2-mod-php perl

Step 2: Define Custom Host Configuration hosts.cfg

sudo nano /usr/local/nagios/etc/hosts.cfg

define host{
    use             linux-server
    host_name       My-Firewall
    alias           FortiGate-60F-Firewall
    address         192.168.1.1   (You can enter your firewall static IP)
}

Step 3: Link Custom Configuration in Main File nagios.cfg

       sudo nano /usr/local/nagios/etc/nagios.cfg

Ensure the configuration path is included:
cfg_file=/usr/local/nagios/etc/hosts.cfg

Step 4: Perform Pre Flight Verification & Restart
       sudo /usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg

Notes Expected Output: Total Errors: 0, Total Warnings: 0

Restart the Nagios service to apply changes:

sudo systemctl restart nagios

*********************** Dashboard & Monitoring Metrics ****************************************

Once configured, access the Nagios Web Interface (http://<server-ip>/nagios/) to verify:

    Host Status: Tracks whether the firewall is UP or DOWN in real-time.

    Packet Loss: Monitors network stability maintained at 0% loss.

    Latency (RTA): Tracks round-trip time delays to identify network congestion.

