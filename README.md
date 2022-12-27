# Tempus Machina
by Morgan Aldridge <morgant@makkintosshu.com>

## OVERVIEW

Tempus Machina aims to provide a macOS (nee OS X) [Time Machine](https://en.wikipedia.org/wiki/Time_Machine_(macOS)) work-alike powered by [rsync](https://rsync.samba.org/), especially the `tmutil` command line utility.

## USAGE

The intent is to support the same `tmutil` command line interface as Apple's native binary:

```
tmutil verb [options]
```

### VERBS

Supported verbs currently include:

* `setdestination [-a] arg`: Set a local mount as a backup destination
  * Requires root
  * If the `-a` option is given, the `arg` will be added to the list of destinations, otherwise `arg` will replace the list of destinations
* `destinationinfo`: Print information about currently configured backup destinations
* `removedestination identifier`: Remove the backup destination with the `indentifier` unique identifier
  * Requires root
* `machinedirectory`: Print the path to the computer's current backup directory
* `listbackups`: Print information about completed backups for this computer
* `addexclusion [-p] item`: Add a file/directory/mount to be excluded from backups
  * Requires root
  * If the `-p` option (currently required) is given, a fixed-path exclusion will be added for `item`
* `removeexclusion [-p] item`: Remove exclusion of file/path/mount from backups
  * Requires root
  * If the `-p` option (currently required) is given, the fixed-path exclusion witll be removed for `item`
* `isexcluded item`: Determine if a file/directory/mount will be excluded from backups
* `startbackup [-b] [-d dest_id]: Manuallly start a new backup
  * Currently requires root
  * If the `-b` option (currently required) is given, it will wait until the backup has completed before exiting
  * If the `-d` option is given, the backup will be performed to the destination with `dest_id` unique identifier
* `latestbackup`: Print information about the computer's most recent backup

Not all of the options that Apple's binary supports are included above. More verbs and options will be added as time permits.

## LICENSE

Released under the [MIT License](LICENSE).
