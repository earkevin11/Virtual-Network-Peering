# Virtual-Network-Peering

# What does VNet peering mean?
- Remember Vnet are isolated by default
- VNet peering connects VNets together! 
- It creates two connections and allow two VNets to communicate with each other\



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


# Disable public IP for staging VM and try to access IIS via its private IP
- Users will see that testingvm cannot access stagingvm because they are on a different network

<p align="center">
  
<img src="" height="100%" width="100%" alt="VNet peering"/>

<p/>


# Create the VNet peering connection
- Networking > select the virtual network > peerings > create new 

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170556235-9505ca49-dea9-46d5-8df5-cbfee1994f06.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

# Configuring the connection
- Here we are connecting the stagingvm to the testvm.
- Select the virtual network you want to link to the current virtual network. It is under Remote Virtual Network section.
- stagingvm -> testvm

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170556752-c2c64e37-db93-4dbb-bbcc-a8fc4bec1800.png" height="100%" width="100%" alt="VNet peering"/>

<p/>


# Install IIS on stagingvm 
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170562384-18c83630-a8dc-43eb-9639-3960def14176.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

# Access IIS via its private IP on testingvm
- Notice that now testingvm can access IIS from stagingvm via the private IP
- This is allowed because of the virtual network peering connection that was created

<p align="center">
  
<img src="" height="100%" width="100%" alt="VNet peering"/>

<p/>



