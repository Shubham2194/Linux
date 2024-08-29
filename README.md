# Linux


Increase EBS Volume Size in AWS
===========================================================
Step 1: Take Snapshot of EBS Volume (to be Safe).

Look after left pannel and find volume section and choose your volume you want to Increase.

![image](https://github.com/user-attachments/assets/169f940d-3167-4123-bebd-25958e72b081)



Step 2: Increase EBS Volume Size in AWS Console.

Go to Ec2 section and find the storage attach to your ec2 instance that we need to modify.


![image](https://github.com/user-attachments/assets/91048292-80a4-498a-bd4e-c95ccd91221f)

(I modified from 8GB to 16GB)


Step 3: Extend a Linux file system after resizing a volume.

Now SSH to your ec2 instance and check volume.

Check the type of our volume and where it is attached to using:
df -hT

(Here we are still seeing that we have 8gb attached RN and i have ext4 file system type and which is mounted to /)


Step 4 :Check whether the volume has a partition:

sudo lsblk

![image](https://github.com/user-attachments/assets/96e6fba7-4a94-41b6-ba06-98751739c2fe)

(we can see we the partition here)



Step 5: Extend the partition:

sudo growpart /dev/xvda 1

This will incase the partition size

Step 6:

Extend the file system on /:

If your file system type is XFS use :
sudo xfs_growfs -d /


and if your file system type is ext4 use:

sudo resize2fs /dev/xvda1

Step 7:

Fire 
df-h / and see the EBS is modified to 20GB.

![image](https://github.com/user-attachments/assets/b0ab0cd2-0b55-4320-85f4-e27f5f7ac600)


Keep Coding !!



