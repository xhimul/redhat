#### Partition Description:
swap : RAM size\
/boot : 1GB\
/tmp : 15GB\
/ : all the other space

#### See present scenery:
#df -hT

#### See used storage:
#du -h\
#du -ch /home/ [directory with grand total]

#### See partition UUID:
#blkid

#### See list partition tables:
#fdisk -l

#### View Specific Disk Partition:
#fdisk -l /dev/sda\
Command (m for help): p [Print all Partition Table]

#### Format a Partition
#mkfs.ext4 /dev/sda4

#### Check Size of a Partition:
#fdisk -s /dev/sda2



* https://www.tecmint.com/check-linux-disk-usage-of-files-and-directories/
* https://www.tecmint.com/find-top-large-directories-and-files-sizes-in-linux/
* https://www.tecmint.com/how-to-check-disk-space-in-linux/
* https://www.tecmint.com/fdisk-commands-to-manage-linux-disk-partitions/

[resize /boot](https://askubuntu.com/questions/280211/how-do-i-resize-my-boot-partition#:~:text=Reboot%20the%20server%20to%20single,new%20size%20with%20additional%201GB.&text=df%20%2Dk%20should%20see%20%2Fboot,to%20print%20the%20partition%20table)
