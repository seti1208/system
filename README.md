#logi serwisu
journalctl -u sshd.service

#jakie są timery:
systemctl list-timers

#kopiuję partycje GPT
sgdisk --backup=/root/sdc_partition_table  /dev/sdc

#przygotowywanie nowego disku dla obrazu
dd if=/dev/zero of=/dev/sdc status=progress count=2099999
#kopiuję partycje na nowy disk
sgdisk --load-backup=/root/sdc_partition_table  /dev/sdc
