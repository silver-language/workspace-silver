Silver-backup
=============

This is a try at a config for a dreamt-of backup management program.


```js
myBackup : Backup
	description:
		This is a config file for silver-backup

	logfile: `~/.log/myBackup.log`

	node:
		disk1:
			path: `/mnt/disk1`
			decsription: `Primary source`
		disk2:
			path: `/mnt/disk2`
			description: `Primary backup`
		disk3:
			path: `/mnt/disk3`
			description: `Secondary backup`
	node end

	operation:
		backup-1-2:
			source: `disk1`
			destination: `disk2`
			method: `send-receive`
			schedule:
				day: 1
			retain: 2
		end

		backup-2-3:
			source: `disk2`
			destination: `disk3`
			method: `send-receive`
			schedule:
				month: 1
			retain: 2
		end
	operation end

myBackup end
```



Schema
------

```js
Backup : Array
	description: String
	logfile: PathString
	node: Array of Node
	operation: Array of Operation
Backup End


Node: Array
	path: PathString
	description: String
Node End

Operation: Array
	source: String
	destination: String
	method: String
	schedule: Array of TimeMarker
	retain: Integer
Operation End

TimeMarker:
	(period): Integer
TimeMarker End
```

I'm really not sure how to define the schedule time markers yet.