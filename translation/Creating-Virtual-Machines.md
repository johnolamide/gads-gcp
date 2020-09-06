# Creating Virtual Machines

## Overview

 In this lab, you will explore the Virtual Machine instance options and create several VMs with different characteristics.

## Objectives

 In this lab, you explore the available options for VMs and see the differences between locations.

 In this lab, you learn how to perform the following tasks:

 - Create several standard VMs

 - Create advanced VMs
 

### Create a Utility Virtual Machine

	gcloud beta compute --project=qwiklabs-gcp-02-8279bb29ce25 instances create vm-instance-1 \
	
	--zone=us-central1-c --machine-type=n1-standard-1 \
	
	--subnet=default --no-address --maintenance-policy=MIGRATE  \
	
	--image=debian-9-stretch-v20200902 --image-project=debian-cloud --boot-disk-size=10GB \
	
	--boot-disk-type=pd-standard --boot-disk-device-name=vm-instance-1 --reservation-affinity=any


### Create a Windows Virtual Machine
	
	gcloud beta compute instances create vm-instance-2 --zone=europe-west2-a --machine-type=n1-standard-2 \
	
	--subnet=default --network-tier=PREMIUM --maintenance-policy=MIGRATE --tags=http-server,https-server \
	
	--image=windows-server-2016-dc-core-v20200813 --image-project=windows-cloud --boot-disk-size=100GB --boot-disk-type=pd-ssd \
	
	--boot-disk-device-name=vm-instance-2 --no-shielded-secure-boot --shielded-vtpm --shielded-integrity-monitoring --reservation-affinity=any

	
	gcloud compute firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default \
	
	--action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server

	
	gcloud compute firewall-rules create default-allow-https --direction=INGRESS --priority=1000 --network=default \
	
	--action=ALLOW --rules=tcp:443 --source-ranges=0.0.0.0/0 --target-tags=https-server

#### Set the password for the Windows VM

##### Click on the name of the windows VM to access 'VM instance details'

##### Then click 'Set Windows Password'

##### Provide a Username, then click 'Set'

##### Copy the provided password and click 'Close'


### Create a Custom Virtual Machine

	gcloud beta compute instances create vm-instance-3 --zone=us-west1-b --machine-type=e2-custom-6-32768 \
	
	--subnet=default --network-tier=PREMIUM --maintenance-policy=MIGRATE  --image=debian-9-stretch-v20200902 \
	
	--image-project=debian-cloud --boot-disk-size=10GB --boot-disk-type=pd-standard --boot-disk-device-name=vm-instance-3 --reservation-affinity=any

### Connect via ssh to your custom VM

	gcloud beta compute ssh --zone "us-west1-b" "vm-instance-3" 

#### To see information about unused and used memory and swap space on your custom VM, run the following command

	free

#### To see details about the RAM installed on your VM, run the following command

	sudo dmidecode -t 17

#### To verify the number of processors, run the following command

	nproc

#### To see details about the CPUs installed on your VM, run the following command

	lscpu

#### To exit the SSH terminal, run the following command

	exit

