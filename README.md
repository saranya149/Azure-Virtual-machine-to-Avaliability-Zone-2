☁️ Azure VM in Availability Zone 2

📍 What it means
Zone 2 is a second, separate datacenter in the same Azure region. It has its own power, cooling and network, so it keeps running even if Zone 1 fails.

⚙️ How it works
• VM-1 runs in Zone 1
• VM-2 runs in Zone 2
• A Load Balancer checks both VMs and sends traffic only to the healthy one
If Zone 1 goes down, Zone 2 takes over automatically.

🛠️ Tools I used
• Azure Portal / Azure CLI
• Ubuntu Linux VM (--zone 2)
• Virtual Network + NSG
• Standard Public IP
• Nginx, SSH

✅ Use cases
• Websites that must stay online
• Backup server for Zone 1
• Production apps with high availability

📊 Uptime (Azure SLA)
VMs in Zone 1 + Zone 2: 99.99%

Key command:
az vm create --resource-group rg-az-lab --name vm-zone2 --image Ubuntu2204 --zone 2 --public-ip-sku Standard

🔗 github.com/saranya149/Azure-virtual-machine-in-linux

Next: adding a Standard Load Balancer in front of both VMs.

#Azure #AvailabilityZones #Linux #CloudComputing #DevOps #LearningInPublic
