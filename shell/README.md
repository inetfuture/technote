# Style Guide

https://google.github.io/styleguide/shell.xml

Highlights & additions & overrides:

```shell
# Write the first line exactly as below:
#!/bin/bash -e

# Prefer camel case naming instead of snake case for vars and functions

# Don't use 'function' keyword when declare functions; google suggested comments style is not necessary
doSomthing() {
  # Use vars with ${xxx} format
  for dir in ${dirs_to_cleanup}; do
    # Always use [[ xxx ]] instead of [ xxx ]
    # Quotes are not necessary except for vars whose value could contain special charaters, like whitespace in paths
    if [[ -d "${dir}" ]]; then
      rm "${dir}"
      # No need to use ${xxx} format for $?, $0, etc
      if [[ $? -ne 0 ]]; then
        logError
      fi
    else
      mkdir -p "${dir}/demo"
      if [[ $? -ne 0 ]]; then
        logError
      fi
    fi
  done
}
```

# [Snippets](./snippets.md)
