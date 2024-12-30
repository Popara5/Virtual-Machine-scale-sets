# Virtual-Machine-scale-sets
Azure virtual machine scale sets let you create and manage a group of load balanced VMs. The number of VM instances can automatically increase or decrease in response to demand or a defined schedule. Scale sets provide high availability to your applications, and allow you to centrally manage, configure, and update a large number of VMs.

In this task, you will deploy an Azure virtual machine scale set across availability zones. VM Scale Sets reduce the administrative overhead of automation by enabling you to configure metrics or conditions that allow the scale set to horizontally scale, scale in or scale out.
In the Azure portal, search for and select Virtual machine scale sets and, on the Virtual machine scale sets blade, click + Create.
On the Basics tab of the Create a virtual machine scale set blade, specify the following settings (leave others with their default values) and click Next : Spot >:
Setting
Value
Subscription
the name of your Azure subscription
Resource group
az104-rg8
Virtual machine scale set name
vmss1
Region
(US)East US
Availability zone
Zones 1, 2, 3
Orchestration mode
Uniform
Security type
Standard
Image
Windows Server 2019 Datacenter - x64 Gen2
Run with Azure Spot discount
Unchecked
Size
Standard D2s_v3
Username
localadmin
Password
Provide a secure password
Already have a Windows Server license?
Unchecked

Note: For the list of Azure regions which support deployment of Windows virtual machines to availability zones, refer to What are Availability Zones in Azure?

On the Spot tab, accept the defaults and select Next : Disks >.
On the Disks tab, accept the default values and click Next : Networking >.
On the Networking page, click the Create virtual network link below the Virtual network textbox and create a new virtual network with the following settings (leave others with their default values). When finished, select OK.
Setting
Value
Name
vmss-vnet
Address range
10.82.0.0/20 (delete the existing address range)
Subnet name
subnet0
Subnet range
10.82.0.0/24

In the Networking tab, click the Edit network interface icon to the right of the network interface entry.
For NIC network security group section, select Advanced and then click Create new under the Configure network security group drop-down list.
On the Create network security group blade, specify the following settings (leave others with their default values):
Setting
Value
Name
vmss1-nsg

Click Add an inbound rule and add an inbound security rule with the following settings (leave others with their default values):
Setting
Value
Source
Any
Source port ranges
*
Destination
Any
Service
HTTP
Action
Allow
Priority
1010
Name
allow-http

Click Add and, back on the Create network security group blade, click OK.
In the Edit network interface blade, in the Public IP address section, click Enabled and click OK.
In the Networking tab, under the Load balancing section, specify the following (leave others with their default values).
Setting
Value
Load balancing options
Azure load balancer
Select a load balancer
Create a load balancer

On the Create a load balancer page, specify the load balancer name and take the defaults. Click Create when you are done then Next : Management >.
Setting
Value
Load balancer name
vmss-lb

Note: Pause for a minute and review what you done. At this point, you have configured the virtual machine scale set with disks and networking. In the network configuration you have created a network security group and allowed HTTP. You have also created a load balancer with a public IP address.
On the Management tab, specify the following settings (leave others with their default values):
Setting
Value
Boot diagnostics
Disable

Click Next : Health >.
On the Health tab, review the default settings without making any changes and click Next : Advanced >.
On the Advanced tab, click Review + create.
On the Review + create tab, ensure that the validation passed and click Create.
Note: Wait for the virtual machine scale set deployment to complete. This should take approximately 5 minutes. While you wait review the documentation.
