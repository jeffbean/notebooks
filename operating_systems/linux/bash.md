


Add user to wheel group
-----------------------
    usermod -G10 user1

Destroy all shared mem spaces
-----------------------------
    ipcrm -a

Locate files without find
-------------------------

    locate <file>

Rsync
-----

rsync -r -a -e "ssh -l root" --delete /home/jbean/puppet/ puppet-master:/etc/puppet/

Make Bootable CDs
-----------------

Mount x86 bootable startsector 63:
mount -t vfat -o ro,loop,offset=32256 Bios.img /mnt2/
