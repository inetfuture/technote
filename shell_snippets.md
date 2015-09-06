## Get dir of the script being executed

```shell
SCRIPT_PATH=$(readlink -f "$0")
SCRIPT_DIR=$(dirname "$SCRIPT_PATH")
```

```shell
CWD=`cd $(dirname $0);pwd`
cd $CWD;
```

## Find nginx master process pid

```shell
ps -ef | grep 'nginx: master' | grep -v grep | awk '{print $2}'
```

```shell
# Squeeze whitespace, cut filed 2 with whitespace as delimiter
ps -ef | grep 'nginx: master' | grep -v grep | tr -s \ | cut -d' ' -f2
```

## Collect hosts' HW and inet addr with ansible

```shell
ansible all -m shell -a 'echo `hostname` `ifconfig | grep eth` `ifconfig | grep 225`' | grep eth | awk '{print $1,$6,$8}' | sed "s/addr://" | sort
```

## Find most memory consuming process then kill it

```shell
PS=`ps -e -opid=,rss=,args= | sort -nk 2 | tail -n 1`
kill -9 `echo $PS | awk '{print $1}'`
```

## Infinite loop

```shell
while :; do date; sleep 1; done;
```

## Print Every Command Executed

```shell
trap 'echo "$BASH_COMMAND"' DEBUG
```

## Batch convert PNG to JPG

```shell
for i in *.png ; do convert "$i" "${i%.*}.jpg" ; done
ls -1 *.png | xargs -n 1 bash -c 'convert "$0" "${0%.*}.jpg"'
ls -1 *.png | parallel --eta convert '{}' '{.}.jpg'
```

## Batch rename files

```shell
find . -type f | sed -n 's/\(.*\)\(TSB\)\(.*\)/mv "\1\2\3" "\1TRE\3"/p' | sh
```
