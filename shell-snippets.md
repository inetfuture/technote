# Get dir of the script being executed

```bash
SCRIPT_PATH=$(readlink -f "$0")
SCRIPT_DIR=$(dirname "$SCRIPT_PATH")
```

# Find nginx master process pid

```bash
ps -ef | grep 'nginx: master' | grep -v grep | awk '{print $2}'
```
