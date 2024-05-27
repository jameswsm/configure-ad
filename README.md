![image](https://github.com/jameswsm/configure-ad/assets/170709350/532c9016-9486-4f51-a45e-fde696c9324f)
</p>

<h1>Active Directory Configuration</h1>
Configuration of Active Directory with Azure VMs.<br />
<br />
Part 1: Setup Resources in Azure <br />
Part 2:


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure Active Subscription (Creation of Reasearch Group, VMs, Virtual Networks, Subnets)
- 
-
-
-
-
-
- 


//When we have a server thats offering services to another computer, in our ex, we have a domain controller offering active directory services, in these cases, we DONT want the ip address to change aka do not get it from dhcp, so we are gonna change domain controller virtual nic ip address from dynamic to static

//We are going to join a client1 computer to the domain, and we want to control DNS settings on this computer, when we create a VM inside an Azure virtual network, the ip addressing is set up automatically, the DNS is set to use the VNET DNS Server, we dont want our client computer to use the VNET DNS serever in this case, we want our client to use the IP ADRESS of the Domain Controller as the DNS server, bc when you install active directory on a server, and turn that server into a domain controller, a dns service is installed as well, and in order for client1 to be able to join the domain, it needs to use the domain controller as its DNS server.

//When we create a VM, it automatically creates a RG and virtual network.

//Domain Controller is just a server/computer that has AD installed on it

//gotta set Domain Controller NIC to static.


<h2>Part 1: (Setup Resources in Azure) Steps: 1 - 12</h2>


![image](https://github.com/jameswsm/configure-ad/assets/170709350/da8825ae-5c75-4817-9c3f-a6b80893da66)
<p>
Step 1: Open Virtual Machines services
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/58fe9355-f4b6-4f06-8f99-dd56ed76c627)
<p>
Step 2: Click Create Azure virtual machine
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/91e37451-2b63-44a5-a40b-0806ae632ab2)
<p>
Step 3: Create new Resource Group and choose a name. (ex: activeDirectory)
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/dc903778-d3f6-4d5d-9c65-67d418de3874)
<p>
Step 4: Enter information, ie: Virtual machine name that we will use for our Domain Controller (ex DC1).
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/223d075a-4202-4aac-8dea-4c2bca30b825)
<p>
Step 5: Choose at least 2 vcpus. Enter a Username/password (ex: labuser). Check in confirmation box below. Click Next.
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/710441f6-cbed-4a08-8575-48a0401e1269)
<p>
Step 7: Click Next: Networking 
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/9b7f2e9f-99a1-4efd-874b-bed49500e690)
<p>
Step 8: Click Review + Create -> Click Create
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/296f7e92-e69c-48a3-a1df-960b246465df)
<p>
Step 9: Navigate back to Virtual Machines -> Create -> Azure virtual machine.  We are going to create our client computer that will join the domain
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/1b5053c6-1a75-4274-9004-ed77a21a47e6)
![image](https://github.com/jameswsm/configure-ad/assets/170709350/c178f7a2-522c-438d-a437-23e5e855064b)
<p>
Step 10: Fill out info ex: Choose RG we created (ex: activeDirectory). Enter name (ex: Client1). Click Review + Create -> Next -> Next: Networking
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/afa02bbb-fe8c-4464-9ad3-4380ef8d7c72)
<p>
Step 11: Virtual Network: Choose the same virtual network as the Domain Controller. (should have been created when we created the DC). Click Review + create -> Create
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/1a14975e-f1d7-4fda-87cd-5282f489a462)
<p>
Step 12: Navigate to Virtual machines -> Click Domain Controller (ex: DC1)
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/af0e36e5-2e4a-449d-a844-18d296d09f1a)
<p>
Step 13: Navigate on the left to Networking -> Network Settings
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/af0e36e5-2e4a-449d-a844-18d296d09f1a)
<p>
Step 14: When we have a server (ex: DC1) that will offer services to another computer, (ex: we have a domain controller offering active directory services), in these cases we DONT want the ip address to change aka do not get it from DHCP, so we are gonna change domain controller virtual nic ip address from dynamic to static. Click on Network interface (ex: dc1190)
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/58d5d1ca-c4e4-4165-b1ed-e4d35c5f20e3)
<p>
Step 15: Click IP configurations.
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/70c37640-dd4e-4d63-87cb-58f351f1cce1)
<p>
Step 16: Here we see the Private IP address is set to dynamic. Lets change this to Static. Click the Name (ex: ipconfig1)
</p>
<br />

![image](https://github.com/jameswsm/configure-ad/assets/170709350/6074648e-5d26-4587-829a-31e98b5bb124)
<p>
Step 17: Change the Private IP address from dynamic to static (ex: 10.0.0.4). Click Save.
</p>
<br />


<p>
Step 18: 
</p>
<br />


















