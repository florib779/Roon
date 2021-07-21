Debian Netinstall

### Post-install

sudo apt-get install ffmpeg cifs-utils curl autofs python3-pip sudo

Login as root:

1. usermod -aG sudo USERNAME
2. reboot

https://confluence.jaytaala.com/display/TKB/Mount+drive+in+linux+and+set+auto-mount+at+boot

* Roon server
  * http://download.roonlabs.com/builds/roonserver-installer-linuxx64.sh
  * chmod +x roonserver-installer-linuxx64.sh
  * sudo ./roonserver-installer-linuxx64.sh
* [Roon-Extension-Manager](https://github.com/TheAppgineer/roon-extension-manager/wiki/Installation#linux)
* Beets (pip)
* Home Assistant
  * File editor
  * Grafana
* Dropbox
* Webmin (AUR)
  * sudo pacman -S webmin
  * Modules
    * Backup Configuration Files
    * Bandwidth Monitoring (3rd)
    * Custom Commands
    * Disk and Network Filesystems
    * File Manager
    * Filesystem Backup
    * Initial System Bootup
    * Log File Rotation
    * MON Service Monitor
    * NFS
    * PostgreSQL Database Server
    * Running Processes
    * SMART Drive Status
    * Samba Windows File Sharing
    * Scheduled Commands
    * Scheduled Cron Jobs
    * Scheduled Webmin Functions
    * Software Package Updates
    * Software Packages
    * System Logs
    * System Status
    * System Time
    * System and Server Status
    * Upload and Download
    * Webmin Configuration
