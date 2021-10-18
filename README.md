# Some Notes For Pi Set-Up

## Getting Going
 * [Rasbien Images](https://www.raspberrypi.com/software/operating-systems/)
 * [Balena](https://www.balena.io/etcher/) (For image Flashing)
 * Enable SSH Access
   * In boot Volume:
     * create empty file named `ssh`
     * create `/etc/wpa_supplicant/wpa_supplicant.conf` (use atom for better line endings). With contents:
     
      ```
      country=us
      update_config=1
      ctrl_interface=/var/run/wpa_supplicant
      network={
        scan_ssid=1
        ssid="MyNetworkSSID"
        psk="Pa55w0rd1234"
      }
      ```
    * Find IP address, add <newHost> to hosts `Windows/System32/driver/etc/hosts`
    * ssh in powershell: pi@<newHost> 
    * password: (rasberry)
    * Copy Authorized key (`C:\Users\<User>\.ssh\id_rsa.pub`) to `~/.ssh/authorized_keys
      * `sudo chown pi:pi ~/.ssh/authorized_keys`
      * `sudo chmod 664 ~/.ssh/authorized_keys`
    * Disable password login: Modify `/etc/ssh/sshd_config` with `PasswordAuthentication no`

  
## Update   

```
sudo apt update
sudo apt full-upgrade
```
  
## Git
Generate SSH Key: `ssh-keygen -b 2048 -t rsa`
