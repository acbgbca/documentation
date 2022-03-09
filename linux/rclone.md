# rclone

## To Install

```
sudo apt-get install rclone
```

## To Setup

From <https://rclone.org/onedrive/>

First, ssh to the box, forwarding port 53682 to the local machine. You need to be able to connect to that port to complete the setup, and it will only accept connections from local host.

To setup a new remote server, run ```rclone config```, then

* Enter a name for the remote
* Select the type of storage (onedrive)
* Leave client_id and client_secret blank
* n for advance config
* y for auto config
* On your local PC, connect to the provided URL
* Select '1' from 'OneDrive Personal or Business'
* Select the number of the provided drive
* y to complete

## To sync a directory

### rclone copy

From <https://rclone.org/commands/rclone_copy/>

rclone copy will copy all files in the source to the destination, ignoring duplicates. It will not remove files.

To use:

```
rclone copy source:sourcepath dest:destpath
```

E.g.

```
rclone copy /nfs/backup/docker onedrive:backup/docker
```

Optional flags:

* -P/--progress - shows progress (useful, as by default nothing is shown in the terminal)
* --dry-run - Emulates what will happen without changing anything
* -i/--interactive - 

### rclone sync

From <https://rclone.org/commands/rclone_sync/>

rclone sync will copy all files in the source to the destination, and delete any files at the destination that don't exist at the source

To use:

```
rclone sync source:sourcepath dest:destpath
```

E.g.

```
rclone sync /nfs/backup/docker onedrive:backup/docker
```

Optional flags:

* -P/--progress - shows progress (useful, as by default nothing is shown in the terminal)
* --dry-run - Emulates what will happen without changing anything
* -i/--interactive - 

## Scheduling Cloud Sync

rclone doesn't schedule its self. Any scheduled cloud syncing needs to occur using a cron job or similar. Note that the cron job needs to run as the same user who ran config as otherwise the configuration will not be present.