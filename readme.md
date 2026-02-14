# SecOps Box Automation
**An Ansible-driven provisioner for hardened Offensive Security environments.**

## Overview
This repository contains a streamlined Ansible playbook to transform a vanilla Kali Linux (or Debian-based) installation into a fully-equipped, structured SecOps workstation. Designed for reproducibility, it automates the deployment of the essential offensive security tools, shell customizations and author-curated selections from the 2025 market.

## Tactical Features
* **System Lifecycle:** Automates `dist-upgrade` and core dependency management.
* **Integrated Tooling:** Auto-provisions industry-standard suites (`Impacket`, `Bloodhound`, `EAPHammer`, etc.) into `/opt`.
* **Environment Optimization:** Customizes `zsh` and developer workflows for efficiency during time-sensitive engagements (e.g., OSCP/HTB).
* **Idempotent Design:** Built to be run multiple times without degrading system state.

## Usage
```bash
ansible-playbook -K main.yml

----

# hypervisor setup
on mac, the regular UTM will also need vagrant installed


* if needed *
```
brew install --cask utm
```

```
brew install hashicorp/tap/hashicorp-vagrant
vagrant plugin install vagrant-utm
```

then add in the ruby code for the vagrant file at the vagrant directory

cp the following json to the vm directory: 
```
{
  "provider": "utm"
}
```

# bringing up the vm

First, ensure Packer is installed on your macOS system (e.g., via Homebrew: brew install packer). 

`brew install packer`

setup the hcl [./kali-utm-build.pkr.hcl](./kali-utm-build.pkr.hcl)

touch http/preseed.cfg

add the checksum to the hcl ^

install packer plugin: 
`packer plugins install  -force  github.com/naveenrajm7/utm`



from this guide: 
https://github.com/icyb3r-code/kali-build

within the kali linux machine:
install Ansible using pip pip3 install ansible.
Clone this repo to your kali linux git clone.
change you current working directory inside kali-build.
```bash
ansible-galaxy collection install community.general
ansible-galaxy install -r requirements.yml --roles-path ./roles --force
sudo whoami
ansible-playbook -i inventory.yml main.yml
```


-----
*DISCLAIMER: For authorized security testing and educational purposes only.*
