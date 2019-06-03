# Linux/Unix Group/User/Ownership Commands

## Group/User

- Note that each user is a member of a *primary group* and zero or more *secondary groups*.
- Locally defined groups are listed in the `/etc/groups` file.


- List all groups
	- `less /etc/groups`
- List groups the current user belongs to
	- `groups`
- Create a new group
	- `sudo groupadd "newGroupName"`
- Change a user's primary group
	- `usermod -g group user`
- Add a user to a secondary group
	- `usermod -a -G newGroup1,newGroup2,... user`
	- `-a`	append
	- `-G`	groups to append user to, separated by commas (no whitespace)


## Ownership

- Change owner of a file
	- `sudo chown user filename.txt`
- Change the group a file belongs to
	- `sudo chgrp group filename.txt`
- Change owner/group recursively (through a directory hierachy)
	- use relevant command with `-R` option

## Permissions

\[Read article on permissions added 2019-04-23 to Devonthink for better information on this gnarly topic!]

`sudo chmod ugo+rwx -R directoryName`

- `-R` for recursive if a directory

