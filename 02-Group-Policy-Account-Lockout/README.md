## 02 - Group Policy for Account Lockout  

## Overview 
Configuring an account lockout policy in Active Directory using Group Policy involves defining settings that control when an account is locked after multiple failed login attempts, how long the account remains locked, and how the lockout counter is reset.


## Step 1: Open the Group Policy Management Console (GPMC)
Log in to Domain Controller (DC-1)
Right Click Start, select <b>RUN</b> and type <b>gpmc.msc</b> in the open box, then press Enter. This opens the Group Policy Management Console.

<img src= "/02-Group-Policy-Account-Lockout/IMG_2648.jpeg">

## Step 2: Create or Edit a Group Policy Object (GPO)
In the GPMC, navigate to the Group Policy Objects section.
Right-click Group Policy Objects and select New to create a new GPO, or right-click an existing GPO and select Edit to modify it.
<img src= "/02-Group-Policy-Account-Lockout/IMG_2649.jpeg">


## Step 3: Navigate to the Account Lockout Policy Settings
In the Group Policy Management Editor, expand the following:
<b>Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy.</b>
<img src= "/02-Group-Policy-Account-Lockout/IMG_2650.jpeg">

## Step 4 : Configure Account Lockout Policy Settings
<b>You will see three primary settings that you need to configure:</b>

1. Account Lockout Duration:
 The time in minutes that an account remains locked before it is automatically unlocked.
Configuration: Double-click on this setting, select Define this policy setting, and then set the duration. 

2. Account Lockout Threshold:
 The number of failed logon attempts that will trigger an account lockout.
Configuration: Double-click on this setting, select Define this policy setting, and then set the threshold.

3. Reset Account Lockout Counter After:
The time in minutes after which the failed logon attempts counter is reset to 0, assuming there are no additional failed logon attempts.
Configuration: Double-click on this setting, select Define this policy setting, and then set the time.

<img src= "/02-Group-Policy-Account-Lockout/IMG_2651.jpeg">


## Step 5 : Update Group Policy
You can wait for the Group Policy to propagate automatically, or you can force an update immediately.
On the client Virtual Machine (client-1) , open Command Prompt and type gpupdate /force, then press Enter.

<img src= "/02-Group-Policy-Account-Lockout/IMG_2654.jpeg">
<img src= "/02-Group-Policy-Account-Lockout/IMG_2655.jpeg">

## Step 6:  Verify the Policy
To verify that policy has been applied , run Command Prompt as administrator and type gpresult /r, then press Enter.
<img src= "/02-Group-Policy-Account-Lockout/IMG_2657.jpeg">
<img src= "/02-Group-Policy-Account-Lockout/IMG_2658.jpeg">
