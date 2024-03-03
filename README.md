# AzureFirewall
In this repository, you will see how to create a firewall blocking ICMP packets in Linux from Windows 10

Before we begin, if you are not familiar with creating Virtual Machines, I encourage you to look at my repository regarding the creation of Virtual Machines. This repository is primarily focused on learning how to block ICMP packets in MS Azure.

![Step 6 connecting the VM1](https://github.com/aaronmjackson/AzureFirewall/assets/119738576/f512d760-b247-47f2-b1cf-d36e1aa450b7)
After creating your two Virtual Machines (Windows 10 & Linux), click the start menu in WIndoes and search for Remote Desktop and connect. Please note you will need to use the username that you created in Azure Virtual Machine 1 (VM1). As you see in the picture above you will need to copy "Public IP address" to connect to the Remote Desktop in Windows. 

![Screenshot 2024-03-03 062535](https://github.com/aaronmjackson/AzureFirewall/assets/119738576/fc49301e-d03e-4c6e-9493-a701fcaa629a)
Here you see I created two Virtual Machines VM1(Windows 10) and VM2(Linux). You will also see NSG (Network Security group) is created for both VMs. A Network Security Group provides a virtual firewall for a set of cloud resources that all have the same security posture. 

![Screenshot 2024-03-03 064741](https://github.com/aaronmjackson/AzureFirewall/assets/119738576/bbe2289e-1388-427a-8749-b6591f224f1e)
Now I am  connected to the Windows 10 Remote desktop.

![Wireshark](https://github.com/aaronmjackson/AzureFirewall/assets/119738576/4403b2f5-b5a1-4a32-9444-266225fe5218)
Go to Explorer and download WireShark.

![Screenshot 2024-03-03 070518](https://github.com/aaronmjackson/AzureFirewall/assets/119738576/efbbcc27-66f5-4f3e-9e8b-b408ee1ca962)
Once in Wireshark, type in "ICMP" in the green search tab. Also, open Powershell in Windows. In PowerShell, you need to "Ping" the private address in VM2 (linux) which is 10.0.0.5. Once completed you will see the protocol ICMP, and info of the request and reply. However, we need to stop the request with a firewall. 

![Screenshot 2024-03-03 071243](https://github.com/aaronmjackson/AzureFirewall/assets/119738576/692bd872-ba77-4f4e-89a5-bb622fc4dab2)
We need to go back to our main desktop and go to VM2-NSG in Azure. 

![Screenshot 2024-03-03 071501](https://github.com/aaronmjackson/AzureFirewall/assets/119738576/1c34537c-4abb-40cc-a338-7fe45e2f044b)
![Step 11 - addingrule](https://github.com/aaronmjackson/AzureFirewall/assets/119738576/361550d2-b320-4a57-98d9-2d2ae00bca70)
To block, the ICMP protocol in Windows 10, we need to go to settings  -> Inbound security rules ->  Add Inbound security rules (See highlights)

![Step 11 - addingrule p2 denying for action](https://github.com/aaronmjackson/AzureFirewall/assets/119738576/fb61b6b8-eadd-4b9b-b502-3458e17b6711)
Make sure you select deny to enable the firewall.

![Screenshot 2024-03-03 072103](https://github.com/aaronmjackson/AzureFirewall/assets/119738576/a90ea9c6-5858-4a50-ab61-fd1ba13e4c65)
Once complete go back to VM1 and you will see under Wireshark "no response found" (highlighted in green), in PowerShell you will see "Request timed out."

This is how you enable the Firewall in Microsoft Azure.

Thank you



