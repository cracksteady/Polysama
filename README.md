# Repository Contents
This repository contains an Ansible playbook designed to install two instances of a Kusama Validator on your Debian/Ubuntu Server.

# Playbook Usage

## Prerequisites
Before using this playbook, ensure the following prerequisites are met:
- SSH access to a machine with a user that has root permissions
- Ansible installed on the machine from which you want to execute the playbook
- Declaration of certain variables
- TCP ports 30344 and 30345 opened to the internet

## Declaration of Variables
### File: 'group_vars/all.yml'
You can modify the following variables in this file:
- `system_username`: Username of your Ubuntu/Debian user
- `kusama_username`: Name for your Kusama Validator and its systemd services
- `version`: Version of the Validator you want to run

### Examples and Explanations
#### system_username
Example:
```
system_username: kusama
```

#### kusama_username
Example:
```
kusama_username: some-name-you-like
```

#### version
Example:
```
version: 1.7.0
```

### File: 'inventory.yml'
You need to modify the following variable in this file:
- `ansible_host`: IP address of your target machine

### Example and Explanation
#### ansible_host
Example:
```
ansible_host: 192.168.1.10
```

# Running the Playbook

## Execute Ansible
Navigate into this repository and run the playbook using the command 'ansible-playbook playbook.yml'.

## Post-Run Verification
Check the logs of your newly created services using the commands 'journalctl -fu kusama-<kusama_username>-1' and 'journalctl -fu kusama-<kusama_username>-2'. Replace `<kusama_username>` with the username you have used in this playbook. The output should resemble the following:
```
⚙️  Syncing 512.4 bps, target=#21918507 (23 peers), best: #1797340 (0x08d0…3cab), finalized #1797203 (0x8387…60f2), ⬇ 417.2kiB/s ⬆ 127.9kiB/s
⚙️  Syncing 423.0 bps, target=#21918508 (23 peers), best: #1799455 (0x0691…446c), finalized #1799168 (0x5440…9498), ⬇ 274.0kiB/s ⬆ 98.4kiB/s
⚙️  Syncing 520.5 bps, target=#21918509 (23 peers), best: #1802060 (0x33db…c62b), finalized #1800710 (0xe30c…3aef), ⬇ 382.8kiB/s ⬆ 111.6kiB/s
⚙️  Syncing 508.6 bps, target=#21918510 (23 peers), best: #1804603 (0x3050…af00), finalized #1804288 (0x5b5f…2431), ⬇ 397.5kiB/s ⬆ 131.6kiB/s
⚙️  Syncing 551.4 bps, target=#21918511 (23 peers), best: #1807360 (0x1746…98f8), finalized #1806336 (0x179a…544e), ⬇ 334.0kiB/s ⬆ 98.3kiB/s
⚙️  Syncing 589.2 bps, target=#2191...
