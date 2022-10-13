+++
title = "How to Install MySQL (MariaDB) on Android With Termux"
date = "2021-02-03"
description = "MariaDB is an open-source database management system, commonly used as an alternative for the MySQL in the LAMP (Linux, Apache, MySQL, PHP/Python/Perl) stack. It is intended to be a drop-in replacement for MySQL."
tags = [
    "termux",
    "mysql",
    "android"
]
cover = "https://res.cloudinary.com/morphy/image/upload/v1612159107/termux-mariadb/mariadb-img_o9mksp.jpg#image"
toc = true
+++

## Introduction

Generally, smartphones are not for programming but with the rapid evolution of technology the capability of smartphone is also increasing. We can do many programming stuffs on smartphone using some applications.

In this blog, we are going to use a database management system in our smartphone using termux.

We cannot run Mysql effeciently on smartphone but alternatively we can use MariaDB as our database management system.
Mysql and mariadb have some similarities and differences.

MariaDB is an open-source database management system, commonly used as an alternative for the MySQL in the LAMP (Linux, Apache, MySQL, PHP/Python/Perl) stack. It is intended to be a drop-in replacement for MySQL.

This tutorial will explain how to install SQL(MariaDB) or MySQL command line Android.

This is a very beginner friendly guide with explanary images.

## Requirements

- Install Termux app ([CLICK HERE](https://play.google.com/store/apps/details?id=com.termux))

- Internet connection

## <ins>Step–1</ins> Updating packages

Okay, so you have installed termux, what next?

Launch termux and this is how termux looks like :

![termux-home-screen](https://res.cloudinary.com/morphy/image/upload/v1612006811/termux-mariadb/termux-home_amfpn1.jpg#image)

First thing you need to do is to allow termux to use device disk storage. To do that run the following command and press allow :

```
termux-setup-storage
```

Now we need to update its initial packages with the following apt command :

```
apt update && apt upgrade
```

In between the updating process if it asks for storage permission or some other permission—just press _Y_ or simply press enter to use defaults.

> You can clear the cluttery screen using `clear` command.

---

## <ins>Step–2</ins> Installing MariaDB (MySQL)

- Run the following command to install mariadb package :

```
pkg install mariadb
```

![installing-mariadb-package](https://res.cloudinary.com/morphy/image/upload/v1612008282/termux-mariadb/install-mariadb_j0bps8.jpg#image)

- Type _Y_ and press enter to give storage permission :

![giving-storage-permission](https://res.cloudinary.com/morphy/image/upload/v1612008593/termux-mariadb/termux-image-2_qhkags.jpg#image)

- Wait until the process completes.

---

## <ins>Step–3</ins> Running/Stopping MariaDB sessions

> You have to use this step every time you need to run MariaDB.

- Run the following command to start mariadb daemon :

```
mysqld_safe -u $(whoami)@localhost
```

- After that your screen will look like this, which means mariadb daemon started successfully :

![starting-mariadb-daemon](https://res.cloudinary.com/morphy/image/upload/v1612011419/termux-mariadb/mariadb-start-cmd-2_gz3fhw.jpg#image)

- Then, press `ctrl+z` or <ins>open a new session</ins> (it means the process will run in background)

- Then, run `mariadb` or `mysql` command to start mariadb-cli :

![mariadb-home-screen](https://res.cloudinary.com/morphy/image/upload/v1612012273/termux-mariadb/mariadb-home_rigrwh.jpg#image)

After running mariadb-cli, do whatever you want — create databases, tables or connect it with python for your projects.

- To exit mariadb, type _exit_ or _quit_

- After exiting MariaDB dont forget to kill the background process completely using the below command (you can also kill sessions using pid's) :

```
killall -u $(whoami)
```

---

## Summary

- Update packages using the below command :

```
apt update && apt upgrade
```

- Install mariadb package using :

```
pkg install mariadb
```

- Start mariadb daemon using :

```
mysqld_safe -u $(whoami)@localhost
```

- Run mariadb using :

```
mariadb
```

Or

```
mysql
```

- Exit mariadb and then kill all background processes (daemons) using :

```
killall -u $(whoami)
```

## Do it using aliases

Optionally, you can also define aliases for above commands in _bash.bashrc_ file like this:

```bash
alias run='mysqld_safe -u $(whoami)@localhost &'
```

```bash
alias stop='killall -u $(whoami)'
```

You don't need to write those long commands every time after using aliases. You just need to type <ins>run, mysql & stop</ins> commands instead.

## Conclusion

In this guide you installed MariaDB to act as an SQL server in android. Optionally, you also created a separate password-authenticated administrative user.

<br>

<style>
img[src$="#image"] {
  border-radius: 10px;
}
</style>
