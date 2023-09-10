# Checklist Hardening Debian/Ubuntu System
#### 1. Update System
Update the system to the latest version by running
- [ ] `Run sudo apt update && sudo apt upgrade -y`

#### 2. Install and Configure Firewall
Install firewall to system by running
- [ ] `sudo apt install ufw`

Enable firewall  by running
- [ ] `sudo ufw enable`

Allow incoming SSH connection by running
- [ ] `sudo ufw allow ssh`

#### 3. Secure SSH
Backup the SSH configuration file by running
- [ ] `sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup`

Open the SSH configuration file in a text editor of your choice. I will use nano by running
- [ ] `sudo nano /etc/ssh/sshd_config`
 - Disable root login by changing PermitRootLogin to no.
 - Change PasswordAunthetication to no.

Restart SSH service by running
- [ ] `sudo systemctl restart ssh`

#### 4. Install and Configure Fail2Ban
Install Fail2Ban by running
- [ ] `sudo apt install fail2ban`

Copy the jail configuration file
- [ ] `sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local` 

Open new jail configuration file in a text editor of your choice. by running
- [ ] `sudo nano /etc/fail2ban/jail.local`
 - Change bantime to 3600
 - Change findtime to 600
 - Change maxretry to 3.

Restart Fail2Ban service by running
- [ ] `sudo systemctl restart fail2ban`

#### 5. Remove Unused Services and Packages
Identify unused packages by running
- [ ] `deborphan`

Remove unused packages by running
- [ ] `sudo apt remove --purge $(deborphan)`

#### 6. Regularly Check for Security Update
Install unattended-upgrades by running
- [ ] `sudo apt install unattended-upgrades`

Enable automatic updates by running
- [ ] `sudo dpkg-reconfigure --priority=low unattended-upgrades`
