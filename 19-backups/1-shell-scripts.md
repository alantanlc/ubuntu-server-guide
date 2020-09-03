# 1. Shell Scripts

One of the simplest ways to backup a system is using a _shell script_. For example, a script can be used to configure which directories to backup, and pass those directories as arguments to the tar utility, which creates an archive file. The archive file can then be moved or copied to another location. The archive can also be created on a remote file system such as an _NFS_ mount.

The tar utility creates one archive file out of many files or directories. tar can also filter the files through compression utilities, thus reducing the size of the archive file.

## 1.1. Simple Shell Script

The following shell script uses tar to create an archive file on a remotely mounted NFS file system. The archive filename is determined using additional command line utilities.

## 1.2. Executing the Script

### 1.2.1. Executing from a Terminal

The simplest way of executing the above backup script is to copy and paste the contents into a file. `backup.sh` for example. The file must be made executable:

```
chmod u+x backup.sh
```

Then from a terminal prompt:
```
sudo ./backup.sh
```

This is a great way to test the script to make sure everything works as expected.

### 1.2.2. Executing with cron

The cron utility can be used to automate the script execution. The cron daemon allows the execution of scripts, or commands, at a specified time and date.

cron is configured through entries in a `crontab` file. `crontab` files are separated into fields:

# m h dom mon dow command
- _m_: minute the command executes on, between 0 and 59.
- _h_: hour the command executes on, between 0 and 23.
- _dom_: day of month the command executes on.
- _mon_: the month the command executes on, between 1 and 12.
- _dow_: the day of the week the command executes on, between 0 and 7. Sunday may be specified by using 0 or 7, both values are valid.
- _command_: the command to execute.

To add or change entries in a `crontab` file the `crontab -e` command should be used. Also, the contents of a `crontab` file can be viewed using the `crontab -l` command.

To execute the `backup.sh` script listed above using cron. Enter the following from a terminal prompt:

```
sudo crontab -e
```

> Using sudo with the `crontab -e` command edits the _root_ user's crontab. This is necessary if you are backing up directories only the root user has access to.

Add the following entry to the `crontab` file:

# m h dom mon dow command
0 0 * * * bash /usr/local/bin/backup.sh

The backup.sh script will now be executed every day at 12:00 am.

> The backup.sh script will need to be copied to the /usr/local/bin/ directory in order for this entry to execute properly. The script can reside anywhere on the file system, simply change the script path appropriately.

For more in-dept crontab options see _Section 1.4, "References" [p. 327].
