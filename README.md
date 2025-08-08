WireGuard Easy Setup Script

A Python-based command-line tool that simplifies installing and managing a WireGuard VPN server on Linux, plus convenient client config helpers (including QR codes). Works on Linux servers; includes limited helpers for Windows hosts.

Features
- Automated installation on Debian/Ubuntu, CentOS/RHEL/Fedora, and Arch (installs wireguard, qrencode, iptables)
- Guided server setup for interface `wg0` with NAT (iptables PostUp/PostDown) and IP forwarding
- Easy peer management: add/remove peers; generates client config and shows a QR code
- View configurations: prints server (`wg0.conf`) and peer configs
- Refresh & Fix: re-detects primary interface, rewrites firewall rules, restarts service
- Full Wipe & Reset: removes WireGuard, configs, and reverts system changes

Paths
- Server config (Linux): `/etc/wireguard/wg0.conf`
- Peer configs (Linux): `/etc/wireguard/peers/<peer>.conf`
- On Windows, configs are stored under: `%USERPROFILE%/WireGuard/peers/<peer>.conf`

Prerequisites
- A Linux server (Debian/Ubuntu, CentOS/RHEL/Fedora, or Arch)
- sudo/root privileges on the server
- Ability to configure UDP port forwarding on your router
- Optional (for QR codes): `qrencode` package

Download and Run
Option A: Use the script already in this repository
```bash
chmod +x ./wireguardsetup
sudo ./wireguardsetup
```

Option B: Download the script directly (replace <URL> with your raw file URL if distributing)
```bash
curl -fsSL <URL-to-raw-wireguardsetup> -o wireguardsetup
chmod +x wireguardsetup
sudo ./wireguardsetup
```

Windows usage (helpers only)
```powershell
# Requires Python 3 installed
python .\wireguardsetup
```
Note: Server installation and management are Linux-only. On Windows, the menu exposes client helpers: Generate Client Config and View Local Client Configs.

Menu Options (Linux)
1. Install WireGuard: Installs required packages for your distro
2. Configure Server (run this first): Creates `wg0`, keys, NAT rules, IP forwarding, and starts the service
3. Add Peer: Creates a peer, assigns next available IP, saves config under peers, and displays a QR code
4. Remove Peer: Lists and removes a peer from `wg0` and deletes its config file
5. View Configurations: Shows server and peer configs
6. Refresh & Fix Server Config: Re-detects primary interface, rewrites PostUp/PostDown, restarts service
7. Full Wipe & Reset: Stops/removes configs and packages; reverts IP forwarding
8. Exit

Port Forwarding (Router)
- Protocol: UDP
- External/WAN Port: the port chosen during setup (default 51820)
- Internal/LAN Port: same as above
- Internal/Device IP: the local IP of your Linux server

Notes
- QR Codes: The script will attempt to display a QR code after generating a client config. If missing, install `qrencode` (e.g., `sudo apt-get install qrencode`).
- DNS: Client configs default to Cloudflare and Quad9 (1.1.1.1, 9.9.9.9).

Disclaimer
This tool performs actions with elevated privileges and modifies system networking. Review and understand the code before running it. Use at your own risk.
