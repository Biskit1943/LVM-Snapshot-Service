# LVM-Snapshot-Service
A simple systemd Service which takes one Snapshot per day at boot Time.
This Script Will take 3 Snapshot and will delete old ones.

# Usage
The Script should have the Followig rights:
```
.rwxrwx---  1.7k root root  20 May 20:34  mk-snapshot*
```

In Words:
```
sudo chown root:root mk-snapshot
sudo chmod 770 mk-snapshot
```

If you set the LVM up as I did in my Installaion explanation 
(here)[https://github.com/Biskit1943/Encrypted-LVM-Arch] you can use this
Script as it is here. If you want to add new Volumes from which to take a
Snapshot or if you have your Volumes named diffrent change the Following Lines:
```
<<< if [ "$1" != "root" ] && [ "$1" != "home" ]; then
>>> if [ "$1" != "<root volume>" ] && [ "$1" != "<home volume>" ]; then

<<< if [ "$1" == "root" ]; then
<<<     REGEX='.?(root)-([0-9]{4}-[0-9]{2}-[0-9]{2}).?'
<<< elif [ "$1" == "home" ]; then
<<<     REGEX='.?(home)-([0-9]{4}-[0-9]{2}-[0-9]{2}).?'
<<< else
<<<     exit -1
<<< fi

Change the names here and add more elif for more snapshots
```

If you want to take more or less Snapshots of each Volume change this Line:
```
<<< if [ ${#NAMES[@]} -ge 3 ]; then
>>> if [ ${#NAMES[@]} -ge X ]; then
```

For other Sizes change the following Lines to your needing:
```
<<< ROOT_SIZE="6G"
<<< HOME_SIZE="6G"
>>> ROOT_SIZE="XG"
>>> HOME_SIZE="XG"

<<< SIZE="1G"
<<< if [ "$1" == "root" ]; then
<<<     SIZE=$ROOT_SIZE
<<< elif [ "$1" == "home" ]; then
<<<     SIZE=$HOME_SIZE
<<< else
<<<     exit -1
<<< fi

Switch Names here to your needings
```

# Issues and Questions
Feel free to post Questions and Issues in the Issue Section
