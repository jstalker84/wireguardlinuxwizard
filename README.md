WireGuard Easy Setup Script 

This is a Python-based command-line tool designed to simplify the installation and management of a WireGuard VPN server on Linux. This script automates the setup of the WireGuard server, the creation of peer configurations, and provides tools for maintenance and troubleshooting.


Features 


Automated Installation: The script automatically detects the Linux distribution (Debian, Ubuntu, CentOS, Fedora, Arch) and installs WireGuard and its dependencies, such as qrencode and iptables.


Guided Server Setup: It provides interactive prompts to help you configure the VPN server, including selecting the network interface and IP address.


Firewall Configuration: The script automatically configures iptables rules for Network Address Translation (NAT), which allows VPN clients (peers) to access the internet and your local network.


Easy Peer Management: You can add new peers with a simple command. It automatically generates client configuration files and displays a QR code for easy import into the WireGuard mobile app.




Configuration Management: The tool lets you view both server and peer configurations. It can also refresh and automatically fix common server misconfigurations, such as incorrect firewall rules.



Clean Uninstallation: A "Full Wipe" option is available to completely remove WireGuard, all configuration files, and revert system changes like IP forwarding.

Prerequisites 

A Linux server with a supported distribution (Debian, Ubuntu, CentOS, Fedora, Arch).

Root (

sudo) privileges on the server.

The ability to configure port forwarding on your router.

Installation and Usage 

1. Download the script: 

You can clone the repository:

Bash

git clone https://github.com/your-username/your-repository-name.git 
cd your-repository-name 
Alternatively, you can download the script directly:

Bash

wget https://raw.githubusercontent.com/your-username/your-repository-name/main/wireguardsetup.py 
chmod +x wireguardsetup.py 
2. Run the script with sudo: 

Bash

sudo ./wireguardsetup.py 
Menu Options 

1. Install WireGuard

: Installs the necessary packages for your distribution. This should be run first on a new system.

2. Configure Server

: This is the essential first step after installation. It guides you through creating the 

wgo interface, generating server keys, and setting up firewall rules.

3. Add Peer

: Creates a new client configuration. You will be prompted to name the peer, and the script will generate the config file and a QR code.

4. Remove Peer

: This option lists all configured peers and allows you to securely remove one.

5. View Configurations

: Displays the current server and peer configurations.

6. Refresh & Fix Server Config

: This non-destructive tool fixes common issues by re-detecting the primary network interface, rewriting firewall rules, and restarting the WireGuard service. It is useful if your server's networking changes.


7. Full Wipe & Reset

: USE WITH CAUTION. This option completely removes WireGuard, all its configuration files, and reverts system changes like IP forwarding.


8. Exit

: Exits the script.

Important: Port Forwarding 

For your VPN to be accessible from the internet, you must set up port forwarding on your router.

Log in to your router's administration page.

Find the "Port Forwarding" or "Virtual Server" section.

Create a new rule with these settings:


Protocol: UDP 


External/WAN Port: The port you chose during the server setup (e.g., 51820) 


Internal/LAN Port: The same port (e.g., 51820) 


Internal/Device IP: The local IP address of your Linux server 

Disclaimer 

This script performs actions with root privileges, including installing software and modifying system network configurations. While it is designed to be safe, you should review the code and understand its function before running it. The author is not responsible for any damage or misconfiguration of your system
