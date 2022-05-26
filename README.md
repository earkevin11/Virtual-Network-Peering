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

<p align="center">
  
<img src="" height="100%" width="100%" alt="VNet peering"/>

<p/>

# Stagingvm should have IIS installed and HTTP open

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170545953-774e0187-30f3-4042-a031-b2db73066766.png" height="100%" width="100%" alt="VNet peering"/>

<p/>

# Ensure both VMs are on their own virtual networks 
- Pay attention to the different virtual networks 
- Stagingvm
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170542909-9ee96139-f7f0-48af-a999-afe50f96b854.png" height="100%" width="100%" alt="VNet peering"/>

<p/>


-testvm

<p align="center">
  
<img src="" height="100%" width="100%" alt="VNet peering"/>

<p/>



# Disable public IP for staging VM and try to access IIS via its private IP
- Users will see that testingvm cannot access stagingvm because they are on a different network

# Create the VNet peering connection

# Access IIS via its private IP on testingvm
- Notice that now testingvm can access IIS from stagingvm via the private IP
- This is allowed because of the virtual network peering connection that was created



