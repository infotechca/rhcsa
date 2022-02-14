# Accessing the Command Line
___

## 1. INTRODUCTION TO THE BASH SHELL

The default shell for users in Red Hat Enterprise Linux is the GNU Bourne-Again Shell (bash).

When a regular user starts a shell, the default prompt ends with a `$` character,  as shown below.

```
haseeb@RHEL8 ~]$
```

The `$` character is replaced by a `#` character if the shell is running as the superuser, root.

The superuser shell prompt is shown below.
```
root@RHEL8 ~]#
```
___

### SHELL BASICS

Commands entered at the shell prompt have three basic parts:

* **Command**
* **Options**
* **Arguments**

For example, the command 
```
haseeb@RHEL8 ~]$ ls -l /etc/fstab
```
**Command**	= `ls`
**Option**		= `-l`
**Argument** = `/etc/fstab`
___
### LOGGING IN TO A LOCAL COMPUTER

The computer might have a hardware keyboard and display for input and output directly connected to it. This is the Linux machine's ***physical console***. The physical console supports multiple ***virtual consoles***, which can run separate terminals. Each virtual console supports an independent login session.

You can switch between them by pressing **Ctrl+Alt** and a function key (**F1** through **F6**)

| Keyboard Shortcut |Using Command		| Virtual Consoles  |
| ----------------- |:-------------:  |:---------------:  | 
| **Ctrl+Alt+F1**   | `chve 1`				| **tty1**					|
| **Ctrl+Alt+F2**   | `chve 2`				| **tty2**					|
| **Ctrl+Alt+F3**   | `chve 3`				| **tty3**					|
| **Ctrl+Alt+F4**   | `chve 4`				| **tty4**					|
| **Ctrl+Alt+F5**   | `chve 5`				| **tty5**					|
| **Ctrl+Alt+F6**   | `chve 6`				| **tty6**					|

The computer might provide a graphical login prompt on one of the virtual consoles. You can use this to log in to a ***graphical environment***. The graphical environment also runs on a virtual console.

The **`who`** command is used to get information about currently logged in user on to system.

```
[haseeb@rhel8 ~]$ who

haseeb   tty2         2022-02-13 13:03 (tty2)
root     tty3         2022-02-13 13:03
user1    tty4         2022-02-13 13:03
user2    tty5         2022-02-13 13:04
user3    tty6         2022-02-13 13:04
```
___
### LOGGING IN OVER THE NETWORK

Linux users and administrators often need to get shell access to a remote system by connecting to it over the network.

In Linux, the most common way to get a shell prompt on a remote system is to use **Secure Shell (SSH)**. Most Linux systems (including Red Hat Enterprise Linux) and macOS provide the **OpenSSH** command-line program `ssh` for this purpose.

```
PS C:\Users\S.A.Haseeb> ssh haseeb@192.168.100.100

The authenticity of host '192.168.100.100 (192.168.100.100)' can't be established.
ECDSA key fingerprint is SHA256:EVoOatN9/Cl3pPy4ZeIosFgOqLm7VSlsi2MDgwOsMXI.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '192.168.100.100' (ECDSA) to the list of known hosts.
haseeb@192.168.100.100's password:

Last login: Sun Feb 13 13:03:15 2022

[haseeb@rhel8 ~]$ who
haseeb   tty2         2022-02-13 13:03 (tty2)
haseeb   pts/1        2022-02-13 13:10 (192.168.100.1)
[haseeb@rhel8 ~]$
```

#### LOGGING OUT
When you are finished using the shell and want to quit.
* You can enter the `exit` command to terminate the current shell session. 
```
[haseeb@rhel8 ~]$ exit
logout
Connection to 192.168.100.100 closed.
PS C:\Users\S.A.Haseeb>
```
* Alternatively,finish a session by pressing **Ctrl+D**.
___
## 2. ACCESSING THE COMMAND LINE USING THE DESKTOP
The ***desktop environment*** is the graphical user interface on a Linux system. The default desktop environment in Red Hat Enterprise Linux 8 is provided by **GNOME**.
**GNOME Shell** provides the core user interface functions for the GNOME desktop environment.

### Parts of the GNOME Shell
![GNOME_Shell](https://github.com/infotechca/rhcsa/blob/main/RH124-I/Images/GNOME_Shell.png?raw=true)

1. **Top bar**
2. **Activities overview**
3. **Dash**: The dash is also sometimes called the **dock**.
4. **Windows overview**
5. **Workspace selector**
6. **Message tray**: The message tray can be opened to review these notifications by pressing **Super+M**.

### WORKSPACES
***Workspaces*** are separate desktop screens that have different application windows. These can be used to organize the working environment by grouping open application windows by task.<br>
To switch between workspaces press: **Ctrl+Alt+UpArrow** or **Ctrl+Alt+DownArrow**.

### STARTING A TERMINAL

To get a shell prompt in GNOME, start a graphical terminal application such as **GNOME Terminal**.<br>
Press the **Alt+F2** key combination to open the Enter a Command and enter **`gnome-terminal`**.

### LOCKING THE SCREEN OR LOGGING OUT

Locking the screen, or logging out entirely.<br>
To lock the screen press: **Super+L** (which might be easier to remember as **Windows+L**).

A ***lock screen curtain*** appears that shows the system time and the name of the logged-in user.<br>
To unlock the screen, press **Enter** or **Space** to raise the lock screen curtain, then enter that user's password on the lock screen.

### POWERING OFF OR REBOOTING THE SYSTEM

To shut down the system press **Ctrl+Alt+Del**.<br>
In the dialog box that displays, you can choose to Power Off or Restart the machine, or Cancel the operation.

## 3. EXECUTING COMMANDS USING THE BASH SHELL

### BASIC COMMAND SYNTAX
The GNU Bourne-Again Shell (**bash**) is a program that interprets commands typed in by the user. Each string typed into the shell can have up to three parts: the ***command***, ***options*** (which usually begin with a **-** or **--**), and ***arguments***. Each word typed into the shell is separated from each other with spaces. Commands are the names of programs that are installed on the system. Each command has its own options and arguments.<br>
<br>
When you are ready to execute a command, press the **Enter** key. Type each command on a separate line. The command output is displayed before the next shell prompt appears.
```
[haseeb@rhel8 ~]$ whoami
haseeb
[haseeb@rhel8 ~]$
```
If you want to type more than one command on a single line, use the semicolon (**`;`**) as a command separator. A semicolon is a member of a class of characters called ***metacharacters*** that have special meanings for **bash**.

The following example shows how to combine two commands (command1 and command2) on the command line.
```
[haseeb@rhel8 ~]$ whoami ; cal
haseeb
    February 2022
Su Mo Tu We Th Fr Sa
       1  2  3  4  5
 6  7  8  9 10 11 12
13 14 15 16 17 18 19
20 21 22 23 24 25 26
27 28

[haseeb@rhel8 ~]$
```
### EXAMPLES OF SIMPLE COMMANDS
* #### `date`
The **date** command displays the current date and time. It can also be used by the superuser to set the system clock. An argument that begins with a plus sign (**+**) specifies a format string for the date command.
```
[haseeb@rhel8 ~]$ date
Mon Feb 14 12:02:19 IST 2022

[haseeb@rhel8 ~]$ date +%r
12:02:24 PM

[haseeb@rhel8 ~]$ date +%x
02/14/2022
```
* #### `passwd`
The `passwd` command changes a user's own password. The original password for the account must be specified before a change is allowed. By default, `passwd` is configured to require a strong password, ***consisting of lowercase letters, uppercase letters, numbers, and symbols, and is not based on a dictionary word***. The superuser can use the `passwd` command to change other users' passwords.
```
[haseeb@rhel8 ~]$ passwd
Changing password for user haseeb.
Current password:
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
```
* #### `file`
Linux does not require file name extensions to classify files by type. The `file` command scans the beginning of a file's contents and displays what type it is. The files to be classified are passed as arguments to the command.

```
[haseeb@rhel8 ~]$ file /etc/passwd
/etc/passwd: ASCII text

[haseeb@rhel8 ~]$ file /usr/bin/passwd
/usr/bin/passwd: setuid ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=c3f73adff4bbb032badae0e967351715bb09ac29, stripped

[haseeb@rhel8 ~]$ file /home
/home: directory
```

### VIEWING THE CONTENTS OF FILES
* #### `cat`
One of the most simple and frequently used commands in Linux is `cat`. The `cat` command allows you to create single or multiple files, view the contents of files, concatenate the contents from multiple files, and redirect contents of the file to a terminal or files.

The example shows how to view the contents of the **/etc/passwd** file.

```
[haseeb@rhel8 ~]$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
...output omitted...
```
Use the following command to display the contents of multiple files.
```
[haseeb@rhel8 ~]$ cat file1 file2
Hello World!
Welcome to InfoTech Computer Academy.
```
* #### `less`
Some files are very long and can take up more room to display than that provided by the terminal. The `cat` command does not display the contents of a file as pages. The `less` command displays one page of a file at a time and lets you scroll at your leisure.<br>

The `less` command allows you to page forward and backward through files that are longer than can fit on one terminal window. Use the **UpArrow key** and the **DownArrow key** to scroll up and down. Press **Q** to exit the command.

* #### `head` and `tail`
The `head` and `tail` commands display the beginning and end of a file, respectively. By default these commands display **10** lines of the file, but they both have a **-n** option that allows a different number of lines to be specified.
```
[haseeb@rhel8 ~]$ head /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin

[haseeb@rhel8 ~]$ tail -n 3 /etc/passwd
tcpdump:x:72:72::/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
haseeb:x:1000:1000:S.A.Haseeb:/home/haseeb:/bin/bash
```
* #### `wc`
The `wc` command counts lines, words, and characters in a file. It takes a **-l**, **-w**, or **-c** option to display only the number of lines, words, or characters, respectively.
```
[haseeb@rhel8 ~]$ wc /etc/passwd
  46  105 2558 /etc/passwd

[haseeb@rhel8 ~]$ wc -l /etc/passwd ; wc -l /etc/group
46 /etc/passwd
70 /etc/group

[haseeb@rhel8 ~]$ wc -c /etc/passwd /etc/group
2558 /etc/passwd
 988 /etc/group
3546 total
```
