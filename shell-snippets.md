## Get dir of the script being executed

```sh
SCRIPT_PATH=$(readlink -f "$0")
SCRIPT_DIR=$(dirname "$SCRIPT_PATH")
```

```sh
CWD=`cd $(dirname $0);pwd`
cd $CWD;
```

## Find nginx master process pid

```sh
ps -ef | grep 'nginx: master' | grep -v grep | awk '{print $2}'
```

```sh
# Squeeze whitespace, cut filed 2 with whitespace as delimiter
ps -ef | grep 'nginx: master' | grep -v grep | tr -s \ | cut -d' ' -f2
```

## Collect hosts' HW and inet addr with ansible

```sh
ansible all -m shell -a 'echo `hostname` `ifconfig | grep eth` `ifconfig | grep 225`' | grep eth | awk '{print $1,$6,$8}' | sed "s/addr://" | sort
```