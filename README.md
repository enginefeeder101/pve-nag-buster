# pve-nag-buster 

This is a dpkg post install hook script that persistently removes license nags
from Proxmox VE 6.x and up. Install it once and you won't see another license
nag until Proxmox changes their web-ui code significantly.

Please support the Proxmox team by [buying a subscription](https://www.proxmox.com/en/proxmox-ve/pricing) if it's within your
means. High quality open source software like Proxmox needs our support!

### How does it work?

The included hook script removes the "unlicensed node" popup nag from the web
gui and disables the pve-enterprise repository list. This script is called
every time a package updates the web gui or the pve-enterprise source list and
will only run if packages containing those files are changed. The installer
creates dpkg hooks to call it then adds the
pve-no-subscription repo list and calls the hook script once. There are no
external dependencies beyond the base packages installed with PVE by default
(awk, sed, grep).

### Installation
```sh
wget https://raw.githubusercontent.com/enginefeeder101/pve-nag-buster/master/pve-nag-buster.sh

# Always read scripts downloaded from the internet before running them with sudo
less pve-nag-buster.sh
chmod +x pve-nag-buster.sh && sudo ./pve-nag-buster.sh --install
```

### Uninstall:
```sh
sudo ./pve-nag-buster.sh --uninstall
# remove /etc/apt/sources.list.d/pve-no-subscription.list if desired
```

### Credits:

Thanks to John McLaren for his [blog post](https://johnscs.com/remove-proxmox51-subscription-notice/) documenting the web gui patch.

### Contact:

[Open an issue](https://github.com/enginefeeder101/pve-nag-buster/issues) on GitHub.
