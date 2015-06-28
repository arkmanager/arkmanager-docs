```
    # Create the ipset list
    ipset -N china hash:net
    ipset -N russia hash:net

    # remove any old list that might exist from previous runs of this script
    rm /etc/block_countries/ips/*.zone

    # Pull the latest IP set for China
    wget -P /etc/block_countries/ips/ http://www.ipdeny.com/ipblocks/data/countries/cn.zone
    # Pull the latest IP set for Russia
    wget -P /etc/block_countries/ips/ http://www.ipdeny.com/ipblocks/data/countries/ru.zone

    # Add each IP address from the downloaded list into the ipset 'china'
    for i in $(cat /etc/block_countries/ips/cn.zone ); do ipset -A china $i; done
    # Add each IP address from the downloaded list into the ipset 'russia'
    for i in $(cat /etc/block_countries/ips/ru.zone ); do ipset -A russia $i; done

    # Restore iptables
    /sbin/iptables-restore < /etc/iptables.firewall.rules
```