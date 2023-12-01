# IOS - Cisco switch OS

Documentation made by Shisuko

## Table of content

- [1 - Modes](#1---modes)
- [2 - Commands](#2---commands)
- [3 - Specifics Configuration](#3---specifics-configuration)
    
    - [3.1 - SSH server](#31---ssh-server)      
    - [3.2 - Update with TFTP](#32---update-with-tftp)
    - [3.3 - Management IP](#33---management-ip)
    - [3.4 - Backup config](#34---backup-config)
	
## 1 - Modes

|       Mode        |       Description     |
|         -         |            -          |
|>|Normal Mode|
|#|Priviliege Mode|
|(config)|Config Mode|
|(config-vlan)|Vlan Config Mode|
|(config-if)|Interface Config Mode|         

## 2 - Commands

|       Mode        |       Command         |       Description         |       Example     |
|         -         |           -           |           -               |          -        |
|||||
|**Modes**|
|>|enable|Switch to priviliege mode|enable|
|#|configure terminal or config t|Switch to configuration mode|configure terminal|
|(config)#|interface \<interface>|Switch to interface configuration mode|interface Fa0/1|
|(config)#|vlan \<vlan>|Switch to vlan configuration mode|vlan 5|
|||||
|**Interfaces**|
|(config-if)#|switchport mode access|force port to an access port|switchport mode access|
|(config-if)#|switchport access vlan \<vlan>|Switch port to a specific vlan|switchport access vlan 3|
|(config-if)#|description \<desription>|set a description to the port|description "MainNet"|
|(config-if)#|switchport mode access|force port to an access port|switchport mode access|
|(config-if)#|speed|change the speed of the port|speed 10|
|(config-if)#|(no) shutdown|(Disable) / Enable port|no shutdown|
|||||
|**Vlans**|
|(config-vlan)#|ip address \<ip> \<mask>|set a management IP for the switch in the vlan|ip address 192.168.1.2 255.255.255.0|
|(config-vlan)#|name \<name>|set a name to the Vlan|name Vlan-Test|
|||||
|**System**|
|(config)#|hostname \<hostname>|Set switch hostname|hostname switch01|
|(config)#|ntp authentificate|Enable NTP|ntp authentificate|
|(config)#|ntp server \<ntp_server_ip>|Set ntp server|ntp server 62.12.167.109|
|#|copy running-config \<configure filename>|copy the current config into a file|copy running-config switch.conf|
|(config)#|vtp mode|set VTP mode|vtp mode transparent|
|>|show|Display information about system|show version|
|#|write|Save running-config to startup-config|write|
|#|reload|Reload the switch|reload|
|(config)#|(no) ip domain-lookup|(Disable) / Enable DNS search for unknow command|no ip domain-lookup|
|any|do|Let you do any command regardless of the mode that you are in|do show running-config|



If you need the option of a command you can use the "?" sign.

```
# show ?

Output :
  access-lists       List access lists
  arp                Arp table
  boot               show boot attributes
  cdp                CDP information
  clock              Display the system clock
  crypto             Encryption module
  dtp                DTP information
  etherchannel       EtherChannel information
  flash:             display information about flash: file system
  history            Display the session command history
  ...

```


## 3 - Specifics Configuration

### 3.1 - SSH server

First of all let's create a user.

    (config)# username <username> password 0 <password>

Then we need to create a domaine.

    (config)# ip domain-name <domain-name>

And finaly we need to generate a RSA key.

    (config)# crypto key generate rsa

We can now SSH into our switch.

### 3.2 - Update with TFTP

You need a management ip to update with tftp

To update a switch you will need a TFTP server. Fist of you need to install a TFTP server like TFTPD64, TFTPD32 or Solarwings TFTP. After you download the TFTP server you will need to download the firmware on the manufacturer website, then launch the tftp server and add the firmware to the TFTP server. Then launch this command on the switch to download the firmware from de server. 

    # copy tftp://<your_tftp_ip_server>/firmware.bin flash:/firmware.bin

Then you can boot with the firmware with this command.

    (config)# boot system firmware.bin

You can now see the the current version.

    # show version

You can now reload the switch with this command.

    # reload

### 3.3 - Management IP

To set a management IP (IP of the switch in the Vlan) you need to create a vlan.

    (config)# vlan 10
    (config-vlan)# name vlan-management

You can now set the Management IP.

    (config-vlan)# ip address 192.168.1.2 255.255.255.0


### 3.4 - Backup config

To backup the config you will need a management IP and TFTP server

To backup the config you will need to save it in a ile first with this command.

    # copy running-config switch.conf

And then send it to the TFTP server.

    # copy flash:/switch.conf tftp://192.168.1.10/switch.conf












<!-- Footer -->

---

Github : https://github.com/shisuko   
Website : http://shisuko.net

---
