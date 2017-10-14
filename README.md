# Systemd Nspawn Container Examples
Example for using systemd container together with unit files for automatic deployment

## Container
### Status of included Containers
|Container|Status|
|-----|-----|
|GitLab|done|
|Transmission|untested, missing start/stop action|
|Nginx|tbd|
|Minecraft|tbd|

### Used Uids/Gids
The first 8 65536-blocks of ids are reserved for the host.
Every container gets a 65536-block of ids assigned.
There are enough ids for 28664 containers.

|Container|First ID|Last ID|#-Range|
|-----|-----|-----|-----|
|Host|0|524287|1-8|
|GitLab|524288|589823|9|
|Transmission|589824|655359|10|
|Mariadb|655360|720895|11|
|Nginx|720896|786431|12|
|...|1878982656|1879048191|28672|

## Asumptions
I'm making some asumptions for this, like specific settings you have to set and pretasks you have to complete first.
Here is a list with some of them:
 - Systemd-networkd is used for initializing and managing your network interfaces
 - Systemd-resolved is used for name resolution (or you would not be able to reach your containers by there name)
 - Everyone hates initd and loves systemd
 - Avoid third party solutions if feasible (too many cooks spoil the broth, thats why I'm doing this instead of using docker)
 - Kernel with user namespace support
 - Systemd Nspawn (not installed on debian based distros by default) apt install systemd-container

## Included Resources
I've included some other modules, because either
a) they are not available on all distributions I use (Archlinux and Debian)
or
b) they are custom ones I wrote and at least one container depends on them (fill an issue if I forgot to include one)

|Resource|Reason|Source|Status|
|-----|-----|-----|-----|
|Systemd Nspawn Unit|not present on Debian, main part|Archlinux|done|
|IPTables Module|Not present on Debian, used for DNat-ing Ports into the container|Archlinux|done|
|IPTables Rules|Some basic iptables rules (review before using!) used to drop malformed traffic and log every connection|agowa338|done|
|Logrotate iptables Rules|There are many logfiles (iptables loggin alone can produce gigabites of uncompressed logs)|agowa338|done|
|Logrotate GitLab Rules|||tbd|
|Logrotate Transmission Rules|||tbd|
|Logrotate Nginx Rules|||tbd|
|Logrotate Minecraft|||tbd|
|Debian Bootstrap Unit|Systemd Unit to bootstrap a new Debian container|agowa338|done|
|ArchLinux Bootstrap Unit|Systemd Unit to bootstrap a new ArchLinux container|agowa338|done|
|Move to Ansible|Because Ansible!||tbd|
