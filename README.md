Azure VM in Availability Zone 1
Overview
A Linux VM created in Availability Zone 1 on Azure. A zone is a separate datacenter inside a region, so the VM is protected from a single datacenter failure.

Architecture

Real-Time Process
User sends a request to the public IP
NSG allows ports 22 and 80
VM in Zone 1 responds with the Nginx page
Steps
Create Resource Group rg-az-lab
Create VM, choose Availability zone → Zone 1
Ubuntu 22.04, Standard_B2s, SSH key
Use a Standard public IP, allow ports 22 and 80
Verify: VM → Overview → Properties → Zone = 1
SSH in and install Nginx
Commands
az group create --name rg-az-lab --location centralindia
az vm create --resource-group rg-az-lab --name vm-zone1 \
  --image Ubuntu2204 --size Standard_B2s --zone 1 \
  --admin-username azureuser --generate-ssh-keys --public-ip-sku Standard
az vm open-port -g rg-az-lab -n vm-zone1 --port 80
sudo apt update && sudo apt install nginx -y
Cleanup
az group delete --name rg-az-lab --yes --no-wait
Tools Used
Azure Portal / CLI, Ubuntu, SSH, Nginx

Author
Saranya T
