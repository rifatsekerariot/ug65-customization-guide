# Scripts

## eth_lan_bridge

Init script that creates a bridge `br-lan` with `wlan0` and `eth0`, assigns `192.168.10.1/24` to the bridge, and restarts the DHCP server so it listens on `br-lan`. Ethernet clients then get DHCP and can use the gateway’s internet (SIM/WiFi).

**Usage (on device as root):**
- Copy this file to `/etc/init.d/eth_lan_bridge`
- `chmod +x /etc/init.d/eth_lan_bridge`
- `/etc/init.d/eth_lan_bridge enable`
- Reboot or run `/etc/init.d/eth_lan_bridge start`

After applying, the gateway will be reachable at **192.168.10.1** (WiFi and Ethernet). You must have root access to install this; this repo does not explain how to obtain root.

## rc_local_dhcpd_brlan.txt

Sample lines to append to `/home/rc.local.custom` so that on each boot the DHCP server is restarted with `br-lan`. Use only if you have already set up the bridge (e.g. via `eth_lan_bridge`).
