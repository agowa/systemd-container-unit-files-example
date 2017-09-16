# systemd-container-unit-files-example
Example for using systemd container together with unit files for automatic deployment

## Asumptions
I'm making some asumptions for this, like specific settings or pre tasks that are performed.
Here is a list with some of them:
 - Systemd-networkd is used for initializing and managing your network interfaces
 - Systemd-resolved is used for name resolution (or you would not be able to reach your containers by there name)
 - Everyone hates initd and loves systemd

## Included examples
 - GitLab-ce
 - Transmission
 - IPTables (Including ruleset)
 - Logrotate
