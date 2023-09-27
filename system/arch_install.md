# Install Arch Linux

Documentation made by Shisuko

*** 

## Summary

1. First of all
2. Arch install
3. Arch config
4. Extra

## 1. First of all
First of all you will need a bootable usb stick with arch linux installed on it. You can download the iso on the official arch website and make the bootable key with refus or balena etcher.

## 2. Arch install
Plug your usb key on your computer and then wait for the grub to start. After that boot into the first option and a terminal should appear.

If you need to change your keyboard layout you can use this command :

```bash
loadkeys <your_layout>
```

First of all you need to check if you have internet connexion : 


```bash
ping google.ch
```

If you have a ethernet connexion this should work. If you need wifi here's how to connect into your wifi in arch install :

```bash
iwctl
```

This should bring you into a menu where you should be abble to config your wifi settings   
For more information : https://www.youtube.com/watch?v=3zqITuprlL8

To sync the time and date use this command :

```bash
timedatectl set-ntp true
```

Now we will partition our disk, use this command to list all disk driver and choose the one where you will install arch :

```bash
lsblk
```

Then we can use this command to partition our disk :

```bash
cfdisk <your_disk>
```

Then we need to choose the label for our disk. If you have a big driver like 500 Go for example you will choose GPT. If you install arch on a small disk or usb you will choose DOS.

Then you can create the partition that you want. I will personnaly create the basics ones :

- 1 for Bootloader (128 Mb)
- 1 for SWAP (1 Go)
- 1 for system (The rest)

Then write and quit cfdisk.
x
We can now format our partition. The bootloader partition and the system partition can be formated in ext4 :

```bash
mkfs.ext4 <your_partition>
```

And then for the swap partition :

```bash
mkswap <your_swap_partition>
swwapon <your_swap_partition>
```

We can now mount our disk :

```bash
mount <your_system_partition> /mnt
```

We can now create a folder for our bootloader : 

```bash
mkdir /mnt/boot
```

And then mount our bootloader partition on that boot folder :

```
mount <your_bootloader_partition> /mnt/boot
```

We can now install arch with pacstrap : 

```bash
pacstrap /mnt base base-devel linux linux-firmware vim
```

This command will install the system and also install package like base, base-devel etc... which are pretty basics packages that you want on linux.

We can now create a FSTab config by this command :
```bash
genfstap -U /mnt >> /mnt/etc/fstab
```

We can now chroot into our installation using this command :

```bash
arch-chroot /mnt /bin/bash
```

We will install grub (boatloader) and network manager : 

```bash
pacman -S networkmanager grub
```

We need to enable the services of the network manager using this command :

```bash
systemctl enable NetworkManager
```

Then install grub :

```bash
grub-install <your_disk> --force
```

And generate config file : 

```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

And there we go you have install arch ! We can now config our Arch.

## 3. Arch config

First of all we can change our password using this command :

```bash
passwd
```

And then config language of the system by editing the /etc/locale.gen with this command :

```bash
vim /etc/locale.gen
```

And the final step is to create a link of your time zone into /etc/localtime : 

```bash
ln -sf /usr/share/zoneinfo/<country>/<city> /etc/localtime
```

You can now install neofetch and enjoy your arch install !

## 4. Extra

In arch there's no sudo group, to use sudo you need to be on the weel group. First of all add your user to the grou by this command :

```bash
usermod -aG wheel <user>
```

Then you need to config the /etc/sudoers file, you need to uncomment this line in the file :

```
# %wheel ALL=(ALL:ALL) ALL
```

Then you should have the sudo working,

***

Twitter : @Shisukkko
