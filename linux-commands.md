# Hardware

- `rfkill`: tool for enabling and disabling wireless devices
- `lshw -C network`
- `lspci / lsusb`: list all PCI / usb devices
- `alsamixer`: soundcard mixer for ALSA soundcard driver, with ncurses interface

# Package

- `dpkg -s`
- `dpkg -c, dpkg -x, dpkg -L`
- `apt-file search`

# Security

- `useradd testuser -m -s /bin/bash`
- `usermod username -G sudo`

# File

- `zip -r dir.zip dir`
- `unzip dir.zip`
- `tar czvf dir.tar.gz dir`
- `tar xzvf dit.tar.gz -C dir`
- `locate`: find files by name, `updatedb`
- `whereis`: locate the binary, source, and manual page files for a command
- `find ./ \( -path ./node_modules -o -path ./.git -o -path ./.idea \) -a -prune -o -print | xargs  wc -l | sort -n`: -a means and, -o means or
- `ls -tr`
- `convmv -r -f cp936 -t utf8 --notest --nosmart *`
- `rsync -lptzr --delete src_dir/ dst_dir`: -l sysmlinks, -p perms, -t times, -z compress

# Disk

- `fdisk -l`: List the partition tables for the specified devices. If no devices are given, those mentioned in /proc/partitions (if that exsts) are used
- `df -h`: report file system disk space usage
- `du -sh target_dir`: estimate file space usage
- `du --max-depth 1 | sort -rn | head -n 5`: top 5 big dir/file

# Network

- `route`: show / manipulate the IP routing table
- `traceroute -I HOST`
- `arp`: manipulate the system ARP cache
- `ip`: show/manipulate routing, devices, policy routing and tunnels
- `nslookup`: query Internet name servers interactively
- `dig`: DNS lookup utility
- `netstat -s | grep -E '.*(queue|timeout).*'`
- `tcpdump -i lo host localhost and port 7070 -A `
- `ss -m src *`
- `cat /proc/net/sockstat：TCP mem about equal ss -m src *`
- `curl ifconfig.me`
- `mtr`: a network diagnostic tool
- `resolvconf -u`
- `nmap -sP 192.168.1.*`

# Service

- `service SCRIPT COMMAND`:  run a System V init script( /etc/init.d/) or an upstart job( /etc/init) (take precedence). 
- `All scripts should supportat least the start and stop command.`
- `upstart jobs`: restart => stop => start, init scripts
- `upstart jobs`: initctl list, init scripts
- `chkconfig`:  enable or disable system services       

# SSH

- `ssh -D [bind local addr`: forward localhost's 7070 port to remotehost    
- `ssh -NfR [bind remote addr`:  forward remotehost's 222 port to localhost's 22 port
- `ssh-keygen -R hostname`: remove all keys belong to hostname from a known_hosts file 
- `ssh-copy-id [-i [identity_file]] username@remotehost`: install your public key in a remote machine's authorized_keys

# VIM

- `set tabstop=4`
- `2yy, p`
- `G or g`:  go to the end/start of the file
- `Ctrl + g`: show file information
- `/ or ?`:  forward or backward search,n or N
- `10j`: 10 lines forward,10k
- `o or O`: insert a new line below or above this line

# GIT

- `git commit --amend`: modify last commit
- `git rebase -i master~3`:   interactive rebase
- `git log：-p --color | --graph | --pretty=oneline`
- `git diff HEAD`: diff staged and unstaged changed files
- `git submodule`, `git add path/to/submodule`
- `git rm --cached path/to/submodule`, `git add path/to/submodule/*`
- `git clone ssh`
- `git clone -b branch_name`
- `git checkout -b branch_name remote/branch_name`, `git checkout --trach remote/branch_name`

# Mail

- `msmtp -S --host serverhost`
- `nslookup -query=mx redhat.com`
- `telnet POP3-server 110`: USER username\n PASS password\n STAT\n LIST\n RETR\n

# PHP

- `pear config-set http_proxy http`

# MongoDB

- `rs.slaveOk()`

# Miscellaneous

- `lsmod`: show  the status of modules in the linux kernel
- `ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime`: set time zone, `date -R`
- `lastlog`: reports the most recent login of all users or of a given user
- `tee`: read from standard input and write to standard output and files
- `php5 --interactive`
- `history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head`
- `gnome-terminal --geometry 110x30+1000+1000 --hide-menubar`
