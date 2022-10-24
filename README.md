# Virtual-Network-Peering

# What does VNet peering mean?
- Remember Vnet are isolated by default
- VNet peering connects VNets together! 
- It creates two connections and allow two VNets to communicate with each other



# How to establish a network peering connection?
- Navigate to the virtual network that the user wants to establish the peering network > peering
- Remember two connections will be established to allow cross connection.



# Use Case: Allow two networks to commmunicate with each other
- Create a virtual network peering connection 

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170547370-0ccdc2bd-38a2-4892-a592-c883a6731b8c.png" height="100%" width="100%" alt="application gateway"/>

<p/>

# Create two networks
- Stagingvm should have IIS installed and HTTP open because IIS web server listens on port 80
- Testvm - no need to open HTTP port 80
- Ensure both VMs are on their own virtual networks 
- Pay attention to the different virtual networks 

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170545953-774e0187-30f3-4042-a031-b2db73066766.png" height="65%" width="65%" alt="VNet peering"/>

<p/>

# Stagingvm virtual network
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170542909-9ee96139-f7f0-48af-a999-afe50f96b854.png" height="100%" width="100%" alt="VNet peering"/>

<p/>


# testvm virtual network

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170547854-df12c410-1f49-408a-8a7d-d0903c16683d.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

# Install IIS on stagingvm 
- Access staging vm on testvm via its public IP address
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170562384-18c83630-a8dc-43eb-9639-3960def14176.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

-stagingvm's public IP

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170575859-9feaa981-ec0c-4d76-9257-310d0cc2235e.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

- IIS webpage

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170575959-12d210a7-8acb-4010-91e3-dcd144eaf0ca.png" height="100%" width="100%" alt="VNet peering"/>

<p/>


# Disable public IP for staging VM and try to access IIS via its private IP on testvm
- Navigate to the virtual network > NIC > IP Configurations > Select the ipconfig1 > Disassociate 

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170576690-eed4aa7b-4894-4913-bd93-4c05772cc356.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

- Notice that there is no public IP for stagingvm

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170576926-1b7bc2c4-dda3-43f0-861e-691c5e4bc173.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

# Access stagingvm using testvm via its private IP
- Since they are on a different network, testvm cannot access stagingvm's webserver via its private IP
- By default, vnets cannot communicate with each other 

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170578196-267d5b9f-d2d3-4736-bbe6-66ead31c5fc8.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

# Create the VNet peering connection
- Networking > select the virtual network > peerings > create new 
- This will allow testvm to access stagingvm via its private IP

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170556235-9505ca49-dea9-46d5-8df5-cbfee1994f06.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

# Configuring the connection
- Here we are connecting the stagingvm to the testvm.
- Select the virtual network you want to link to the current virtual network. It is under Remote Virtual Network section.
- stagingvm -> testvm
- Notice that two connections will be created on both stagingvm and testingvm

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170556752-c2c64e37-db93-4dbb-bbcc-a8fc4bec1800.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

# Access IIS via its private IP on testingvm
- Notice that now testingvm can access IIS from stagingvm via the private IP
- This is allowed because of the virtual network peering connection that was created
- Below is the peer connection created for stagingvm
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170579211-65f445f1-29ad-49bb-a7f4-619d5f433856.png" height="150%" width="150%" alt="VNet peering"/>

<p/>

- This peer connection is created for testvm

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170579179-7ed5bad4-fd49-4159-b715-5a024fc1489c.png" height="150%" width="150%" alt="VNet peering"/>

<p/>

- Congrats! The virtual network peering connectiong was successful
- testvm can now access stagingvm webserver via its private IP
- Vnet peering connections allows the cross network communication

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170579812-d290109a-cff3-4d18-97e6-421c539317b5.png" height="100%" width="100%" alt="VNet peering"/>

<p/>





