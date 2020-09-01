# 1. User Management

User management is a critical part of maintaining a secure system. Ineffetive user and privilege management often lead many systems into being compromised. Therefore, it is important that you understand how you can protect your server through simple and effective user account management techniques.

## 1.1. Where is root?

Ubuntu developers made a conscientious decision to disable the administrative root account by default in all Ubuntu installations. This does not mean that the root account has been deleted or that it may not be accessed. It merely has been given a password which matches no possible encrypted value, therefore may not log in directly by itself.

Instead, users are encouraged to make use of a tool by the name of sudo to carry out system adminstrative duties. Sudo allows an authorized user to temporarily elevate their privilege using their own password instead of having to know the password belonging to the root account. This simple yet effective methodology provides accountability for all user actions, and gives the administrator granular control over which actions a user can peform with said privileges.

- If for some reason you wish to enable the root account, simply give it a password:

> Configurations with root passwords are not supported.

```
sudo passwd
```

Sudo will prompt you for your password, and then ask you to supply a new password for root as shown below:

```
[sudo] password for username: __(enter your own password)__
Enter new UNIX password: __(enter a new password for root)__
Retype new UNIX password: __(repeat new password for root)__
passwd: password updated successfully
```

- To disable the root account password, use the following passwd syntax:
```
sudo passwd -l root
```

However, to disable the root account itself, use the following command:
```
usermod --expiredate 1
```

- You should read more on Sudo by reading the man page:
```
man sudo
```

By default, the initial user created by the Ubuntu installer is a member of the group _"sudo"_ which is added to the file `/etc/sudoers` as an authorized sudo user. If you wish to give any other account full root access through sudo, simply add them to the _sudo_ group.
