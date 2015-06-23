RHEL/CentOS 6.6 and below have an outdated version of glibc and gcc, you can make ARK server works manually upgrading these libraries:

# prerequisites
```ssh
yum groupinstall "Development tools"
yum install glibc-devel.i686 glibc-i686
```

# glibc

```ssh
cd /tmp
wget http://ftp.gnu.org/gnu/glibc/glibc-2.16.0.tar.gz
tar -xvzf glibc-2.16.0.tar.gz
cd glibc-2.16.0
mkdir glibc-build
cd glibc-build
../configure --prefix='/usr'
```

We have to fix a little typo, so run:

```ssh
nano +171 ../scripts/test-installation.pl
```
and **replace** `if (/$ld_so_name/) {` with `if (/\Q$ld_so_name\E/) {`

then install it:

```ssh
make
sudo make install
```

# gcc

This operation takes a lot of space! be sure to have enough!

```ssh
cd /tmp
wget ftp://ftp.gwdg.de/pub/misc/gcc/releases/gcc-4.6.4/gcc-4.6.4.tar.gz
tar -xvzf gcc-4.6.4.tar.gz
cd gcc-4.6.4
./contrib/download_prerequisites
mkdir objdir
cd objdir
../configure --prefix=/opt/gcc-4.6.4
make
make install
mv /usr/lib64/libstdc++.so.6 /usr/lib64/libstdc++.so.6.bak
mv /opt/gcc-4.6.4/lib64/libstdc++.so.6 /usr/lib64/libstdc++.so.6
mv /opt/gcc-4.6.4/lib64/libstdc++.so.6.0.16 /usr/lib64/libstdc++.so.6.0.16
```

Credits:
http://steamcommunity.com/app/346110/discussions/0/594820656473094010/