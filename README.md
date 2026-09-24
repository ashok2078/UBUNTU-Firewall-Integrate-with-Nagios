 1. Project Overview

    The main objective of this project is to set up a central monitoring server Nagios Core on Ubuntu and use it to track the live availability,        uptime, and network latency RTA of an enterprise grade firewall FortiGate 60F

2. Environment & Tools Used

   * Monitoring Server: Ubuntu Linux running Nagios Core

   * Target Network Device: FortiGate Firewall

   * Protocols & Tools: ICMP (Ping), TCP, Git & GitHub for Version Control

3. Step-by-Step Implementation Process

   Step 1 Nagios Core Prerequisites & Installation

          Installed required packages on the Ubuntu server Apache, PHP, build tools, etc.

          Downloaded, compiled, and installed Nagios Core from source, and enabled the systemd service.

   Step 2: Custom Host Configuration hosts.cfg

          Created a custom configuration file to define the network firewall inside Nagios

##  Repository Structure
    text
    nagios.cfg        # Main Nagios configuration file (includes custom host definitions)
    hosts.cfg         # Custom host configuration file for the FortiGate firewall
    README.md         # Project documentation
