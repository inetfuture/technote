# Package

- `dpkg -c`: list contents of deb package,` dpkg -x`: extract files from package, `dpkg -L`: list files installed from a package-name
- `dpkg -s filename`: search for a filename from *installed* packages
- `apt-file search filename`: search which package contains a specific file/path
- `apt-get -o Dpkg::Options::="--force-confmiss" install --reinstall <package-name>`

# File

- `zip -r dir.zip dir [-x dir/node_modules\* dir/.git\*]`
- `unzip dir.zip`
- `tar czvf dir.tar.gz dir [--exclude node_modules --exclude .git]`
- `tar xzvf dit.tar.gz -C dir`
- `tar`: omit `-v` to see error info, filename should follow `-f` directly
- `locate`: find files by name, `updatedb`
- `whereis`: locate the binary, source, and manual page files for a command
- `find ./ \( -path ./node_modules -o -path ./.git -o -path ./.idea \) -a -prune -o -print | xargs  wc -l | sort -n`: -a means and, -o means or
- `find . -mtime +30 | xargs rm -rf`: delete files older than 30 days
- `ls -tr`
- `convmv -r -f cp936 -t utf8 --notest --nosmart *`
- `iconv -f UTF-16LE -t UTF-8 utf-16leEncodiedFile > output`
- `rsync -lptzr --delete src_dir/ dst_dir`: -l sysmlinks, -p perms, -t times, -z compress

# Text

- `sort -k3 -r -n -h`: -k3 => third column, -r reverse, -n numeric sort, -h human numeric sort
- `tr`: translate or delete characters
- `sed -i 's/ugly/beautiful/g' filename`: edit file in place to replace ugly with beautiful
- `strings`: pint the strings of printable characters in files
- `expand`: convert tabs to spaces
- `tee`: read from standard input and write to standard output and files
- `grep -r "word" /path/to/dir/*.c`, `find . -type f -exec grep -l "word" {} +`, `find /path/to/dir -type f -print0 | xargs grep -l "foo"`: recursively search all files for a string, `find -print0` can deal with spaces in file names
- `egrep -v 'exclude1|exclude2'`
- `find -L /etc/ssl/certs -type l -delete`

# Disk

- `fdisk -l`: List the partition tables for the specified devices. If no devices are given, those mentioned in /proc/partitions (if that exsts) are used
- `df -h`: report file system disk space usage
- `du -sh target_dir`: estimate file space usage
- `du --max-depth 1 | sort -rn | head -n 5`: top 5 big dir/file
- `mount -t cifs -o username=USERNAME,password=PASSWORD //HOST/SHARE_NAME /mnt/MOUNT_POINT`: mount smb share folder
- `hdparm -t /dev/sda6`: perform timings of device reads for benchmark and comparison
- `blockdev --report`: print a report for the specified device
- `blockdev --getra /dev/sda`, `blockdev --setra /dev/sda`: get/set readahead, in sectors
- `blockdev --getbsz /dev/sda`, `blockdev --setbsz /dev/sda`: get/set block size, in bytes
- `lsblk -o NAME,PHY-SeC`, `cat /sys/block/sda/queue/physical_block_size`: get block device physical sector size

# Network

## Config

- `resolvconf -u`
- `route`: show / manipulate the IP routing table
- `route add -net 10.0.0.0 netmask 255.0.0.0 gw 192.168.225.173`: add static route
- `arp`: manipulate the system ARP cache
- `arp -D test6; arp -d test6; arp -s test6 MAC_addr`
- `dig +short HOSTNAME`

## Diagnose

- `ip`: show/manipulate routing, devices, policy routing and tunnels
- `curl ifconfig.me`: figure out external ip
- `ip -4 route get 8.8.8.8`: figure out which interface is used to comunicate with certain host
- `traceroute -I HOST`
- `nslookup`: query Internet name servers interactively
- `dig`: DNS lookup utility
- `mtr`: a network diagnostic tool
- `netstat -s | grep -E '.*(queue|timeout).*'`
- `tcpdump -i lo host localhost and port 7070 -A -s 0`
- `ss -m src *`
- `cat /proc/net/sockstat：TCP mem about equal ss -m src *`
- `nmap -sP 192.168.1.*`

# Service

- `service SCRIPT COMMAND`:  run a System V init script(/etc/init.d/) or an upstart job(/etc/init) (take precedence).
- `All scripts should supportat least the start and stop command.`
- `upstart jobs`: restart => stop => start, init scripts
- `upstart jobs`: initctl list, init scripts
- `update-rc.d SCRIPT enable/disable`, `chkconfig`:  enable or disable system services

# SSH

- `ssh -NfD [local_addr]:7070`: forward localhost's 7070 port to remotehost, dynamically
- `ssh -NfL [local_addr]:7070:remote_addr:22 user@remotehost`: forward localhost's 7070 port to remotehost's 22 port, default local_addr is loopback
- `ssh -NfR [remote_addr:]7070:local_addr:22 user@remotehost`:  forward remotehost's 7070 port to localhost's 22 port, default remote_addr is loopback, if want it to be the others, turn `GatewayPorts` on in `/etc/ssh/ssd_config`, then `reload ssh`
- `ssh-keygen -R hostname`: remove all keys belong to hostname from a known_hosts file
- `ssh-copy-id [-i [identity_file]] username@remotehost`: install your public key in a remote machine's authorized_keys

# GIT

- `git commit --amend --author "name <email>"`: modify last commit
- `git rebase -i master~3`:   interactive rebase
- `git log：-p --color | --graph | --pretty=oneline`
- `git diff HEAD`: diff staged and unstaged changed files
- `git submodule`, `git add path/to/submodule`, `git rm --cached path/to/submodule
- `git clone -b branch_name`
- `git checkout -b branch_nae remote/branch_name`, `git checkout --trach remote/branch_name`
- `git remote prune origin`, `git remote update`
- rewrite commit histroy

    ```bash
    git filter-branch --commit-filter '
    if [ "$GIT_COMMITTER_NAME" = "wrong_name" ];
    then
        GIT_COMMITTER_NAME="inetfuture(Aaron Wang)";
        GIT_AUTHOR_NAME="inetfuture(Aaron Wang)";
        GIT_COMMITTER_EMAIL="inetfuture@gmail.com";
        GIT_AUTHOR_EMAIL="inetfuture@gmail.com";
        git commit-tree "$@";
    else
        git commit-tree "$@";
    fi' HEAD
    ```

# VIM

- `set tabstop=4`, `set nospell`
- `2yy, p`
- `G or g`:  go to the end/start of the file
- `Ctrl + g`: show file information
- `/ or ?`:  forward or backward search, `n or N`: next or previous
- `10j`: 10 lines forward,`10k`: 10 lines backward
- `o or O`: insert a new line below or above this line

# Mail

- `msmtp -S --host serverhost`: check information about SMTP server
- `nslookup -query=mx redhat.com`
- `telnet POP3-server 110`: commands: user, pass, stat, list, retr, dele(take effect after quit), quit

# openssl

- openssl x509 -text -noout -in PEM_FILE_PATH

# PHP

- `php --ini`: show configuration file names
- `php --interactive`
- `php -m | grep ext_name`: check extension
- `php-config `: get information about PHP configuration and compile options
- `pear config-set http_proxy http`

# Hardware

- `rfkill`: tool for enabling and disabling wireless devices
- `lshw -C network`
- `lspci / lsusb`: list all PCI / usb devices
- `alsamixer`: soundcard mixer for ALSA soundcard driver, with ncurses interface

# Performance Monitoring

- `iostat -xm 2`
- `iotop`

# Miscellaneous

- `lsmod`: show the status of modules in the linux kernel
- `ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime`: set time zone, `date -R`
- `useradd testuser -m -s /bin/bash`
- `usermod username -Ga sudo`, `groups username`
- `lastlog`: reports the most recent login of all users or of a given user
- `history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head`
- `gnome-terminal --geometry 110x30+1000+1000 --hide-menubar`
- `update-alternatives --config editor`
- `x11vnc --create --forever`
