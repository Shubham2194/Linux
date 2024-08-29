# Linux


Increase EBS Volume Size in AWS
===========================================================
Step 1: Take Snapshot of EBS Volume (to be Safe).





Step 2: Increase EBS Volume Size in AWS Console.




Step 3: Extend a Linux file system after resizing a volume.


df -hT

Step 4 :Check whether the volume has a partition:
sudo lsblk

Step 5: Extend the partition:
sudo growpart /dev/xvda 1

Step 6:
Extend the file system on /:
[XFS file system]: sudo xfs_growfs -d /
[Ext4 file system]: sudo resize2fs /dev/xvda1


Keep Coding!!
