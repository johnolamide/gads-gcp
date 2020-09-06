# Google Cloud Fundamentals: Getting Started with Compute Engine

## Objectives

 In this lab, you will learn how to perform the following tasks

 - Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

 - Create a Compute Engine virtual machine using the gcloud command-line interface.

 - Connect between the two instances.


### Create a Virtual Machine Using the GCP console (Translated to code)

	gcloud beta compute instances create my-vm-1 --zone=us-central1-a --machine-type=e2-medium --subnet=default --tags=http-server --image=debian-9-stretch-v20200902 --image-project=debian-cloud --boot-disk-size=10GB --boot-disk-type=pd-standard --boot-disk-device-name=my-vm-1 --reservation-affinity=any

	gcloud compute firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server

### Create a Virtual Machine Using the GCloud Command Line Interface

#### To display a list of zones in the region 'us-central1'
	
	gcloud compute zones list | grep us-central1
	
	
#### Choose 'us-central1-b' from the list of zones in the region
	
	gcloud config set compute/zone us-central1-b
	
	
#### Create a VM instance called my-vm-2 in that zone

	gcloud compute instances create "my-vm-2" --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default"

	
#### Close the shell by executing the command
	
	exit

### Connect between VM Instances

#### Connect the 'my-vm-2' instance by ssh using the command

	gcloud beta compute ssh --zone "us-central1-b" "my-vm-2" 
	
#### Ping 'my-vm-1' using the command
	
	ping my-vm-1
	
#### Abort the operation by pressing CTRL+C

#### Use ssh command to open a command prompt in my-vm-1

	ssh my-vm-1
	
#### Install Nginx web server on my-vm-1

	sudo apt-get install nginx-light -y
	
#### Use the nano text editor to add a custom message to the home page of the web server

	sudo nano /var/www/html/index.nginx-debian.html
	
#### Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this, and replace YOUR_NAME with your name

	Hi from YOUR_NAME
	
#### Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the nano text editor.

#### Confirm that the web server is serving your new page. At the command prompt on my-vm-1, execute this command:

	curl http://localhost/
	
#### To exit the command prompt on my-vm-1, execute this command:

	exit
	
#### To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, execute this command:

	curl http://my-vm-1/
	
