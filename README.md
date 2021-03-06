# zpool-scrub
Service and Timer for zpool scrub on Ubuntu

## Install on Ubuntu
- Clone this repository, change into the directory zpool-scrub-weekly
- Install and enable timer and service file in /etc/systemd/system:
```shell
git clone https://github.com/stesind/zpool-scrub.git
cd zpool-scrub

sudo install -m 644 -o root -g root zpool-scrub@.service /etc/systemd/system
sudo install -m 644 -o root -g root zpool-scrub@.timer /etc/systemd/system

sudo systemctl daemon-reload
sudo systemctl enable --now zpool-scrub@<POOLNAME>.timer
```
Replace &lt;POOLNAME&gt; with the name of your pool.
Keep in mind that the path is /sbin/zpool in Ubuntu. On Arch Linux it is /usr/sbin/zpool. One has to change the service file accordingly if not used in Ubuntu. If you are unsure about the location, find out using:
  ```shell
  which zpool
  ```
