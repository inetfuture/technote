# GUI

- KDocker, put any window into tray.
- Email notification: thunderbird(FireTray) + xfce4-notifyd

# Server

- http://www.thekelleys.org.uk/dnsmasq/doc.html, a lightweight, easy to configure DNS forwarder and DHCP server.

# zsh

```
autoload -U up-line-or-beginning-search
autoload -U down-line-or-beginning-search
[[ -n "${key[Up]}" ]] && bindkey "${key[Up]}" up-line-or-beginning-search
[[ -n "${key[Down]}" ]] && bindkey "${key[Down]}" down-line-or-beginning-search
```
