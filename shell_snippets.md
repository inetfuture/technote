# Get dir of the script being executed

```shell
SCRIPT_PATH=$(readlink -f "$0")
SCRIPT_DIR=$(dirname "$SCRIPT_PATH")
```

```shell
CWD=`cd $(dirname $0);pwd`
cd $CWD;
```

# Find nginx master process pid

```shell
ps -ef | grep 'nginx: master' | grep -v grep | awk '{print $2}'
```

```shell
# Squeeze whitespace, cut filed 2 with whitespace as delimiter
ps -ef | grep 'nginx: master' | grep -v grep | tr -s \ | cut -d' ' -f2
```

# Collect hosts' HW and inet addr with ansible

```shell
ansible all -m shell -a 'echo `hostname` `ifconfig | grep eth` `ifconfig | grep 225`' | grep eth | awk '{print $1,$6,$8}' | sed "s/addr://" | sort
```

# Find most memory consuming process then kill it

```shell
PS=`ps -e -opid=,rss=,args= | sort -nk 2 | tail -n 1`
kill -9 `echo $PS | awk '{print $1}'`
```

# Infinite loop

```shell
while :; do date; sleep 1; done;
```

# Print Every Command Executed

```shell
trap 'echo "$BASH_COMMAND"' DEBUG
```

# Batch convert PNG to JPG

```shell
for i in *.png ; do convert "$i" "${i%.*}.jpg" ; done
ls -1 *.png | xargs -n 1 bash -c 'convert "$0" "${0%.*}.jpg"'
ls -1 *.png | parallel --eta convert '{}' '{.}.jpg'
```

# Batch rename files

```shell
find . -type f | sed -n 's/\(.*\)\(TSB\)\(.*\)/mv "\1\2\3" "\1TRE\3"/p' | sh
```

# Count lines while ignoring some folders

```shell
find . -name "*.h" -o -name "*.m" -path ThirdParties -prune | xargs cat | wc -l
```

# Download markdown links

```shell
grep 'http' ../README.md | sed "s/.*\(http.*g\).*/\1/" | xargs wget --restrict-file-names=nocontrol
```

# Kill orphan processes

```shell
ps -elf | awk '{if ($5 == 1){print $4" "$5" "$15}}' | grep php | egrep -v 'php-fpm' | awk '{print $1}' | xargs kill
```

# Grep but always show first line

```shell
awk 'NR == 1 || /php/'
```

# View output of a process

```shell
strace -e write=1,2 -e trace=write -p 7214
```

# Convert .mov to .gif

https://gist.github.com/dergachev/4627207

```shell
ffmpeg -i in.mov -s 800x600 -pix_fmt rgb8 -r 10 -f gif - | gifsicle --optimize=3 --delay=3 > out.gif
```

# Ensure ssh tunel

```shell
ps -ef | grep "ssh -NfR 127.0.0.1:3033:local:80 remote" | grep -v grep
if [[ $? != 0 ]]; then
  log 'Start tunnel on remote'
  ssh -NfR 127.0.0.1:3033:local:80 remote
fi
```
