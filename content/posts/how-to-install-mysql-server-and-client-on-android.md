+++
title = "How to Install MySQL Server and Client on Android"
date = "2021-02-26"
description = "Install MySQL on android without an error. MySQL is a relational database management system, which is based on SQL. The most common use of MySQL is a web database."
tags = [
    "termux",
    "mysql",
    "mariadb",
    "android"
]
cover = "https://www.techtalkthai.com/wp-content/uploads/2019/06/mariadb_banner.png#image"
+++

If you are still stucked in installation of MySQL (MariaDB) on your android — don't worry we have a quick and best solution for that.

We have already done a tutorial on this topic : [How to Install MySQL (MariaDB) on Android With Termux](https://thetechnohack.cf/post/how-to-install-mysql-on-android-with-termux/) <br>
But this tutorial on how to install mysql is going to be far more easy and straightforward than our old tutorial.

We made a simple tool (bash scripting) to solve this problem, which automates all the processes and you only need to use some easy instructions commands.

> **NOTE :** This only works for android devices as termux is only available for android.

## Installation

1. Install Termux App ([Click Here](https://play.google.com/store/apps/details?id=com.termux))

2. Open Termux Application

3. Copy & Paste The Below Command :

```shell
apt update && apt upgrade; pkg install wget; cd ..; wget -O mysql.tar.gz "https://github.com/sumit-buddy/mysql-for-termux-android/archive/v1.0.tar.gz"; tar -xzf mysql.tar.gz -C home --strip-components 1 && rm mysql.tar.gz && cd home && rm -r images && rm README.md; chmod u+x installer.sh; ./installer.sh; source ~/../usr/etc/bash.bashrc; rm installer.sh
```

4. Now the installation will begin. <br>
   (**Please be patient as this may take some time depending on your internet speed**)

5. You will be asked to answer
   <ins>`Do you want to continue? [Y/n]`</ins>
   upto three times. Each time type in '_y_' and press enter.

6. After that, the following pop-up will appear. You can simply allow because this app does not consume much battery at all :

![stop optimizing battery usage?](https://raw.githubusercontent.com/sumit-buddy/mysql-for-termux-android/master/images/stop-optimizing-battery-usage.jpg#image)

7. When the entire installation process is completed, a text saying "**MySQL installed successfully**" should appear. <br>
   Now, the MySQL server has started on your machine and you are all set to use MySQL.

## Commands

- <ins>start-server</ins>

```shell
start-server
```

Run this command to start MySQL server. (**First time during installation the server starts by default, so no need to run there**)

- <ins>setpass</ins>

```shell
setpass
```

Use this command to set a password for the user. (**This can only be done while the server is running.**)

- <ins>start-client</ins>

```shell
start-client
```

Run this command to start the MySQL client.

- <ins>stop-server</ins>

```shell
stop-server
```

Use this command to stop MySQL server (daemon). <br>
**Must use this command to stop MySQL server after exiting mariadb, otherwise when you try to start the server again you will get the error : `Error 2002 (HY000)`**

## Troubleshooting Errors

1. If you get any errors during or after installation, you can check the log file using the command:

```shell
cat logs.log
```

2. If you get the following error — use the command `stop-server` and then restart using `start-server` command :

```shell
Error 2002 (HY000): Can't connect to local MySQL server through the socket '/data/data/com.termux/files/usr/tmp/mysqld.sock' (111)
```

If you're still finding it difficult or having some error, you can send a screenshot of your error and ask for help...

<style>
img[src$="#image"] {
  border-radius: 10px;
}
</style>

<br>
