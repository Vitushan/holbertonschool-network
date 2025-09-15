# 0-change_your_home_IP

This script updates the `/etc/hosts` file to:
- Change `localhost` from `127.0.0.1` to `127.0.0.2`
- Change `facebook.com` to `8.8.8.8`

A backup of the original `/etc/hosts` is created.

---

## Example Usage

Before running the script:

```bash
$ ping -c 1 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.012 ms
--- localhost ping statistics ---
1 packets transmitted, 1 received, 0% packet loss

$ ping -c 1 facebook.com
PING facebook.com (157.240.11.35) 56(84) bytes of data.
64 bytes from edge-star-mini-shv-02-lax3.facebook.com (157.240.11.35): icmp_seq=1 ttl=63 time=15.4 ms
--- facebook.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss

$ sudo ./0-change_your_home_IP
Backup of /etc/hosts saved to /etc/hosts.bak.2025-09-15_19:55:23

$ ping -c 1 localhost
PING localhost (127.0.0.2) 56(84) bytes of data.
64 bytes from localhost (127.0.0.2): icmp_seq=1 ttl=64 time=0.012 ms
--- localhost ping statistics ---
1 packets transmitted, 1 received, 0% packet loss

$ ping -c 1 facebook.com
PING facebook.com (8.8.8.8) 56(84) bytes of data.
64 bytes from facebook.com (8.8.8.8): icmp_seq=1 ttl=63 time=8.06 ms
--- facebook.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss

$ sudo cp /etc/hosts.bak.<timestamp> /etc/hosts
