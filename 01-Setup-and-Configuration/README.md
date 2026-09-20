## 01 — Setup and Configuration

## Overview

This section documents the setup and configuration of the Active Directory Helpdesk Lab in Microsoft Azure.

The environment consists of a Windows Server 2022 virtual machine (DC-1) configured as the Domain Controller and a Windows client virtual machine (Client-1) used to simulate an end user’s workstation.

The machines communicate through an Azure Virtual Network and are configured within Active Directory domain.

##  Phase 1: Azure Environment Setup

## 1. Create Azure Resource Group

Creating a dedicated Azure Resource Group to contain the virtual machines, networking resources, and other components used throughout the lab.
<img src="1/Screenshot 2026-09-19 104615.png" >


## 2. Create Virtual Network

Creating an Azure Virtual Network and subnet for communication between DC-1 and Client-1.

<img src="1/Screenshot 2026-09-19 104846.png" >


## 3. Create DC-1

Deploying a Windows Server 2022 virtual machine named DC-1.

This server will later be configured as the Active Directory Domain Controller.
<img src="1/Screenshot 2026-09-19 105955.png" >
 <img src="1/Screenshot 2026-09-19 110006.png">
 <img src="1/Screenshot 2026-09-19 110032.png">
  <img src="1/Screenshot 2026-09-19 110354.png">
    <img src="1/Screenshot 2026-09-19 110425.png">
 



## 4. Create Client-1

Deploying a Windows 10/11 virtual machine named Client-1 using the same Azure Virtual Network as DC-1.

This VM represents an employee workstation.

<img src="1/Screenshot 2026-09-19 205639.png" >
<img src="1/Screenshot 2026-09-19 210542.png" >




## 5. Configure DC-1 Networking

Configuring the private IP address of DC-1 so that it can be consistently used by Client-1 for DNS and Active Directory communication.

<img src="1/Screenshot 2026-09-19 212252.png" >


<img src="1/Screenshot 2026-09-19 212400.png" >
<img src="1/Screenshot 2026-09-19 212551.png" >



## 6. Test Connectivity

Verifiing network connectivity between DC-1 and Client-1 using their private IP addresses.

 Example: ping <DC-1-private-IP>

Successful connectivity confirms that the two machines can communicate over the Azure Virtual Network.

<img src="1/Screenshot 2026-09-20 014540.png" >
<img src="1/Screenshot 2026-09-20 014729.png" >

<img src="1/Screenshot 2026-09-20 014816.png" >

##  Phase 2: Active Directory Domain Setup
## Step 1: Install "Active Directory" on DC-1. Set up DC-1 as a new domain.
<img src= "/IMG_2619.jpeg">

## Step 2: Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
<img src= "/IMG_2620.jpeg">
<img src= "/IMG_2621.jpeg">

## Step 3: Restart and then Remote Desktop back into DC-1 as user: mydomain.com\labuser

##Step 4: In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES” and “_ADMINS” 

<img src= "/IMG_2622.jpeg">
<img src= "/IMG_2624.jpeg">

## Step 5: Create a new employee named “Jane Doe” (same password) with the username of “jane_admin” to the _ADMINS OU. Then add jane_admin to the “Domain Admins” Security Group 

<img src= "/IMG_2626.jpeg">
<img src= "/IMG_2627.jpeg">
<img src= "/IMG_2628.jpeg">

## Step 6: Log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\jane_admin”

<img src= "/IMG_2630.jpeg">

## Step 7: Join Client-1 DNS to your domain (mydomain.com).</p>

<img src= "/IMG_2631.jpeg">
<img src= "/IMG_2632.jpeg">

## Step 8: Login to Client-1 as the original local admin (labuser) and join it to the domain (computer will restart)


## Step 9: When Client-1 restarts log back in (Remote Desktop) as mydomain.com\jane_admin and verify that client-1 shows up in ADUC.

<img src= "/IMG_2634.jpeg">

## Step 10: Use Remote Desktop in the system settings to allow domain users access for all non-admin users on Client-1 VM under "remote desktop" --> "select users or groups that can remotely access this PC" --> click "add" and type in "domain users". 
<img src= "/IMG_2636.jpeg">
<img src= "/IMG_2637.jpeg">



## Step 11: Login to DC-1 as jane_admin
<img src= "/IMG_2639.jpeg">

 ## Step 12: Open PowerShell_ise as an administrator
<img src= "/IMG_2640.jpeg">

## Step 13: Copy and paste this [Script]("https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1"). This will create new users with random names. This is done to simulate employees within the company.

<img src= "/IMG_2641.jpeg">
<img src= "/IMG_2642.jpeg">

## Step 14: Pick any of the newly generated user and login on Client-1 VM. The login attempt with the user's name and generic password from the script should be successful.
<img src= "/IMG_2643.jpeg">
<img src= "/IMG_2645.jpeg">
<img src= "/IMG_2646.jpeg">










