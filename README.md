# AWS-EBS-HANDSON
CREATING EBS VOLUME , ATTACHING AND DITTACHING EBS, MOUNTING EBS TO DIFFERENT EC2 INSTANCE,
CREATING SNAPSHORT, CREATING VOLUME OUT OF SNAPSHOT TO DIFFERENT AZ, COPYING SNAPSHORT TO ANOTHER REGION TO CREATE VOLUME

# Commands User  

## Instance 1

lsblk
sudo file -s /dev/xvdf
sudo mkfs -t xfs /dev/xvdf
sudo file -s /dev/xvdf
sudo mkdir /ebstest
sudo mount /dev/xvdf /ebstest
cd /ebstest
sudo nano amazingtestfile.txt
add a message
save and exit
ls -la

## Reboot Instance 1

sudo reboot

## Instance 1 After Reboot

df -k
sudo blkid
sudo nano /etc/fstab
  ADD LINE 
  UUID=YOURUUIDHEREREPLACEME  /ebstest  xfs  defaults,nofail
sudo mount -a
cd /ebstest
ls -la

## Instance 2

lsblk 
sudo file -s /dev/xvdf
sudo mkdir /ebstest
sudo mount /dev/xvdf /ebstest
cd /ebstest
ls -la

## Instance 3

lsblk 
sudo file -s /dev/xvdf
sudo mkdir /ebstest
sudo mount /dev/xvdf /ebstest
cd /ebstest
ls -la

## InstanceStoreTest

lsblk
sudo file -s /dev/nvme1n1 
sudo mkfs -t xfs /dev/nvme1n1
sudo file -s /dev/nvme1n1
sudo mkdir /instancestore
sudo mount /dev/nvme1n1 /instancestore
cd /instancestore
sudo touch instancestore.txt

## InstancStoreTest - After Restart

df -k
its not there
but we can mount it
sudo mount /dev/nvme1n1 /instancestore
cd /instancestore
ls -la

## InstanceStoreTest - After Stop/Start

sudo file -s /dev/nvme1n1
