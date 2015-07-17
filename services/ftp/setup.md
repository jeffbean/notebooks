FTP
===

restore ssh key access denied
-----------------------------

    restorecon -R -v /root/.ssh/


To allow ftp home dirs in selinux
---------------------------------

    setsebool -P ftp_home_dir on

iptables rules
--------------
/etc/sysconfig/iptables-config

    IPTABLES_MODULES="ip_conntrack_ftp"

/etc/sysconfig/iptables

    #FTP rules
    #
    -A INPUT -p tcp --dport 21 -j ACCEPT
    -A OUTPUT -p tcp --sport 20 -j ACCEPT

    #ssh rules
    -A INPUT -p tcp -m state --state NEW -m tcp --source 192.168.0.1/16 --dport 22 -j ACCEPT
    -A INPUT -p tcp --dport 22 -j DROP
