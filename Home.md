Welcome to the ark-server-tools wiki!

### Before creating a issue, please do the following:

* Make sure to go through the steps of the [README](https://github.com/FezVrasta/ark-server-tools#ark-survival-evolved-linux-server-tools).
* Check if your problem can be solved by reading any of the existing [issues](https://github.com/FezVrasta/ark-server-tools/issues) to avoid creating duplicates.

#### Troubleshooting

**lsof: command not found**

On CentOS/Fedora/Red Hat etc, lsof is located in /usr/bin. You need to specify it's path before running it as a non-root user: 

```$ /usr/sbin/lsof /path/to/some/file```

On Debian based distros, the lsof package is not installed by default. You have to manually install it:

```$ sudo apt-get install lsof```