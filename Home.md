Welcome to the ark-server-tools wiki!

### Before creating a issue, please do the following:

* Make sure to go through the steps of the [README](https://github.com/FezVrasta/ark-server-tools#ark-survival-evolved-linux-server-tools).
* Check if your problem can be solved by reading any of the existing [issues](https://github.com/FezVrasta/ark-server-tools/issues) to avoid creating duplicates.
* Check the troubleshooting section below.

### Troubleshooting

Make sure to check your server logs for hints.

#### lsof: command not found

On CentOS/Fedora/Red Hat etc, lsof is located in /usr/bin. You need to specify it's path before running it as a non-root user: 

```$ /usr/sbin/lsof /path/to/some/file```

On Debian based distros, the lsof package is not installed by default. You have to manually install it:

```$ sudo apt-get install lsof```


#### /lib64/libc.so.6: version `GLIBC_2.14' not found

You're missing a dependency. Install atleast glibc-2.15 on your server.

See [Install of required versions of glibc and gcc on RHEL CentOS](Install-of-required-versions-of-glibc-and-gcc-on-RHEL-CentOS)

#### `GameUserSettings.ini` is being overwritten and is losing all my settings

Make sure your `GameUserSettings.ini` contains the following 2 lines:

```
[/Script/ShooterGame.ShooterGameUserSettings]
Version=5
```

If the above doesn't work, make sure you haven't put any non-ascii characters into `GameUserSettings.ini`.