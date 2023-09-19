# Installation of MySQL on Debian

Documentation made by Shisuko

*** 

## Summary

1. Add MySQL repository   
1.1 Update your system   
1.2 Install dependencies   
1.3 Download the package   
1.4 Execute the package   
2. Installa MySQL   
2.1 Download the package     
2.1 Check server status   
3. Configure MySQL   
3.1 Launch configuration   
3.2 Test MySQL


# 1. Add MySQL repository

## 1.1 Update your system

First of all update/grade the package of your system

```bash
sudo apt update && sudo apt upgrade -y
```

## 1.2 Install dependencies

Install dependencies to install MySQL

```bash
sudo apt install wget gnupg
```

## 1.3 Download the package

```bash
wget https://dev.mysql.com/get/mysql-apt-config_0.8.22-1_all.deb
```

## 1.4 Execute the package

```bash
sudo chmod +x mysql-apt-config_0.8.22-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.22-1_all.deb
sudo apt update
```

# 2. Installa MySQL

## 2.1 Download the package

```bash
sudo apt install mysql-server
```

## 2.1 Check server status

```bash
sudo systemctl status mysql
```

If the service is running you can go to the next step

# 3. Configure MySQL

## 3.1 Launch configuration

```bash
mysql_secure_installation
```

## 3.2 Test MySQL

```bash
sudo mysql -u root -p
```







***

Twitter : @Shisukkko
