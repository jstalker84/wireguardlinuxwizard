WireGuard Easy Setup Script
A Python-based command-line tool to simplify the installation and management of a WireGuard VPN server on Linux. This script automates the setup of a WireGuard server, the creation of peer configurations, and provides tools for maintenance and troubleshooting.

Features
Automated Installation: Automatically detects the Linux distribution (Debian, Ubuntu, CentOS, Fedora, Arch) and installs WireGuard and its dependencies (qrencode, iptables).

Guided Server Setup: Interactive prompts to configure the VPN server, including network interface and IP address selection.

Firewall Configuration: Automatically configures iptables rules for NAT, allowing VPN clients (peers) to access the internet and the local network.

Easy Peer Management:

Add new peers with a simple command.

Automatically generates client configuration files.

Displays a QR code for easy import into the WireGuard mobile app.

Configuration Management:

View server and peer configurations.

Refresh and automatically fix common server misconfigurations (e.g., incorrect firewall rules).

Clean Uninstallation: A "Full Wipe" option to completely remove WireGuard, all configuration files, and revert system changes (like IP forwarding).

Prerequisites
A Linux server running a supported distribution (Debian, Ubuntu, CentOS, Fedora, Arch).

Root (sudo) privileges on the server.

The ability to configure port forwarding on your router.

Installation and Usage
Download the script:

git clone https://github.com/your-username/your-repository-name.git
cd your-repository-name

or download it directly:

wget https://raw.githubusercontent.com/your-username/your-repository-name/main/wireguardsetup.py
chmod +x wireguardsetup.py

Run the script with sudo:

sudo ./wireguardsetup.py

Menu Options
Install WireGuard: Downloads and installs the necessary packages for your distribution. Run this first on a new system.

Configure Server: The essential first step after installation. This will guide you through creating the wg0 interface, generating server keys, and setting up firewall rules.

Add Peer: Creates a new client configuration. You will be asked to name the peer, and the script will generate the config file and a QR code.

Remove Peer: Lists all configured peers and allows you to securely remove one.

View Configurations: Displays the current server configuration and the configurations for all peers.

Refresh & Fix Server Config: A non-destructive tool to fix common issues. It re-detects the primary network interface, rewrites the firewall rules, and restarts the WireGuard service. This is useful if your server's networking changes.

Full Wipe & Reset: USE WITH CAUTION. This completely removes WireGuard, all its configuration files, and reverts system changes like IP forwarding.

Exit: Exits the script.

IMPORTANT: Port Forwarding
For your VPN to be accessible from the internet, you must set up port forwarding on your router.

Log in to your router's administration page.

Find the "Port Forwarding" or "Virtual Server" section.

Create a new rule with the following settings:

Protocol: UDP

External/WAN Port: The port you chose during the server setup (e.g., 51820).

Internal/LAN Port: The same port (e.g., 51820).

Internal/Device IP: The local IP address of your Linux server.

Disclaimer
This script performs actions with root privileges, including installing software and modifying system network configurations. While it is designed to be safe, please review the code and ensure you understand what it does before running it. The author is not responsible for any damage or misconfiguration of your system.
