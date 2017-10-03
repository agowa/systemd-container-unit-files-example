# systemd-container-unit-files-example
Example for using systemd container together with unit files for automatic deployment

# Container
## Status of included Containers
|Container|Status|
|-----|-----|
|GitLab|done|
|Transmission|untested, separate from nspawn unit|
|Nginx|tbd|
|Minecraft|tbd|

## Used Uids/Gids
The first 8 65536-blocks of ids are reserved for the host.
Every container gets a 65536-block of ids assigned.
There are enough ids for 28664 containers.

|Container|First ID|Last ID|#-Range|
|-----|-----|-----|-----|
|Host|0|524287|1-8|
|GitLab|524288|589823|9|
|Transmission|589824|655359|10|
|...|1878982656|1879048191|28672|
