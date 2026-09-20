## 01 — Setup and Configuration

## Overview

This section documents the setup and configuration of the Active Directory Helpdesk Lab in Microsoft Azure.

The environment consists of a Windows Server 2022 virtual machine (DC-1) configured as the Domain Controller and a Windows client virtual machine (Client-1) used to simulate an end user’s workstation.

The machines communicate through an Azure Virtual Network and are configured within Active Directory domain.

##  Phase 1: Azure Environment Setup

## 1. Create Azure Resource Group

Creating a dedicated Azure Resource Group to contain the virtual machines, networking resources, and other components used throughout the lab.

<p align="center">
  <img src="" width="700" style="border-radius:10px; border:1px solid #ccc;" />
  <img src="" width="700" style="border-radius:10px; border:1px solid #ccc;" />
</p>


## 2. Create Virtual Network

Creating an Azure Virtual Network and subnet for communication between DC-1 and Client-1.

<p align="center">
  <img src="" width="700" style="border-radius:10px; border:1px solid #ccc;" />
</p>



## 3. Create DC-1

Deploying a Windows Server 2022 virtual machine named DC-1.

This server will later be configured as the Active Directory Domain Controller.

<p align="center">
  <img src="" width="700" style="border-radius:10px; border:1px solid #ccc;" />
</p>




## 4. Create Client-1

Deploying a Windows 10/11 virtual machine named Client-1 using the same Azure Virtual Network as DC-1.

This VM represents an employee workstation.

<p align="center">
  <img src="" width="700" style="border-radius:10px; border:1px solid #ccc;" />
</p>



## 5. Configure DC-1 Networking

Configuring the private IP address of DC-1 so that it can be consistently used by Client-1 for DNS and Active Directory communication.

<p align="center">
  <img src="" width="700" style="border-radius:10px; border:1px solid #ccc;" />
</p>



## 6. Test Connectivity

Verifiing network connectivity between DC-1 and Client-1 using their private IP addresses.

 Example: ping <DC-1-private-IP>

Successful connectivity confirms that the two machines can communicate over the Azure Virtual Network.

<p align="center">
  <img src="" width="700" style="border-radius:10px; border:1px solid #ccc;" />
</p>

