ESX
===

Print License
-------------

    vim-cmd vimsvc/license --show | grep serial | awk '{print $2}'

Power on all vms
----------------

    for i in `vim-cmd vmsvc/getallvms | awk '{ print $1 }'`; do vim-cmd vmsvc/power.on $i ; done


Autostart a vm
--------------
vim-cmd hostsvc/autostartmanager/update_autostartentry

    Usage: update_autostartentry VMId StartAction StartDelay StartOrder StopAction StopDelay WaitForHeartbeat

    vim-cmd hostsvc/autostartmanager/update_autostartentry <vm number> poweron <delay for on> <autostart order nubmer> stop <stop delay> no
    vim-cmd hostsvc/autostartmanager/update_autostartentry 1 poweron 90 1 stop 90 no
