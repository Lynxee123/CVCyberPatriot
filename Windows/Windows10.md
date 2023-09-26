[winlogo]:./Images/microsoft.png


# Basic Windows Checklist

Refer to README.md for more information

This is a gui walkthrough which you may use as a guide when developing automation scripts

Complete these steps **in order** for best results (If possible, script all of them to make your life easier)

## Forensics Questions: 

One Question usually involves encryption/cipher.  
Refer to this webpage for decryption:
[cryptii](https://cryptii.com)

Other questions involve searching for malicious files and services  
This usually hinders progress so get it done first  
**(even if it's hard, you'll learn more from searching than you will from giving up)**

## Windows Update:
* **Windows Key** &rarr; **Settings** &rarr; **Windows Update** &rarr; **Check for Updates** 
	* (Don't skip no matter how long it takes)  
  

Make sure it completes before you move on (will make everything else less stressful)

While waiting for windows update, take the time to document all the users and administrators from the readme, as well as any passwords they do not want you to change. You will have to remove accounts laters as well as change account passwords so that they comply with the password policies you will setup.

## Firewall:

* **Windows Key** &rarr; **Windows Security** &rarr; **Firewall & Network Protection** &rarr; **Turn On**

## Remote Assistance:

* **Windows Key + R** &rarr; **control** &rarr; **System** &rarr; **Remote Settings** &rarr; **Allow Remote Assistance connections to this computer** (uncheck) &rarr; **Okay**
	
## Account Policy

* **Windows Key + R** &rarr; **secpol.msc**
* Under **Account Policies**

#### Password Policy:

* Under **Password Policy**
* Enforce Password History: **24 passwords remembered**  
* Maximum password age: **90 days**  
* Minimum password age: **3 days**  
* Minimum password length: **14 characters**  
* Password must meet complexity requirements: **Enabled**  
* Store passwords using reversible encryption: **Disabled**  

#### Account Lockout Policy:

* Under **Acount Lockout Policy**
* Account Lockout Threshold: **10**
* Account lockout duration and reset lockout: **30 Minutes**
## Local Policies

* Under **Local Policy**

#### Audit Policy

* All: **Success, Failure**

#### User Rights Assignment

* Anything out of place (user's acting as part of the operating system, etc), remove them and document your findings

## Security Options:
* Under **Security Options**
### Accounts:

* Administrator Account status: **Disabled**
* Guest Account status: **Disabled**
* Limit local account use of blank passwords to console only: **Enabled**
* Limit local use of blank passwords to console only: **Enabled**

### Devices:

* Allow undock without having to log on: **Disabled**

### Interactive Logon:

* Display user information when the session is locked: **Do not display user information**
* Do not require CTRL+ALT+DEL: **Disabled**
* Don't display last signed-in: **Enabled**

### MS Network CLient:

* Digitally sign communications (always): **Disabled**

### Network Access:

* Allow anonymous SID/Name translation: **Disabled**
* Do not allow anonymous enumeration of SAM accounts: **Enabled**
* Do not allow anonymous enumeration oof SAM accounts and shares: **Enabled**
* Let Everyone permissions apply to anonymous users: **Disabled**
* Restrict anonymous access to Named Pipes and Shares: **Enabled**

### Network Security:

* Do not store LAN Manager hash value on next password change: **Enabled**

### Recovery Console:

* Allow automatic admin logon: **Disabled**
* Allow floppy copy and access to all drives and all folders: **Disabled**

### Shutdown: 

* Allow system to be shutdown without having to logon: **Disabled**

### User Account Control:

* Admin Approval Mode for Built-in Administrator account: **Enabled**
* Behavior of the Elevation prompt for standard users automatically: **Deny**
* Run all administrators in Admin Approval Mode: **Enabled** 
	* this setting may take up time when it comes to doing administrative tasks, so I recommend to set this last after finding as many vulnerabilities as you can

## Advanced Audit Policy Configuration:

* Everything: **Success, Failure**
	* Exception: Global Object Access Auditing - **Leave Alone**

## Users:

* **Windows Key + R** &rarr; **lusrmgr.msc**

### Remove Unauthorized Users (Documented during windows update):

* **Users &rarr; right click on user &rarr; Delete**

### Add new users (Documented during windows update):

* **Users &rarr; More Actions &rarr; New User &rarr; add applicable settings (documented from readme)**

### Change user properties

* **Users &rarr; right click on user &rarr; change password**
	* (**example: P@ssword123456789**)
 	* Password must follow complexity rules set earlier 	

* **Users &rarr; right click on user &rarr; Properties**

	* User must change password at next logon: **checked**   
		* exception: admin account  
	* User cannot change password: **unchecked**
	* Password never expires: **unchecked**
	* Account is disabled: **unchecked** 
		* exception: administrator and guest accounts
	* Account is locked out: **unchecked**
	
## Groups:

### Remove unauthorized users

* **Groups &rarr; right click on group &rarr; properties &rarr; Select user &rarr; remove**

### Create groups (in readme):

* **Groups &rarr; more actions &rarr; new group &rarr; applicable settings**

### Add users to groups (in readme):

* **Groups &rarr; right click on group &rarr; properties &rarr; add &rarr; enter user name**

### Remove unnecessary groups

* **Groups &rarr; right click on group &rarr; Delete**   
	* **do not delete windows default groups, specified by their complex names indicating they are part of the operating system**

## File Shares:

* **Windows Key + R** &rarr; **fsmgmt.msc**

### Shares:

* **Shares** &rarr; right click on share &rarr; stop sharing
	* Exceptions: shares ending in "$" 

### Sessions:

* **Top Left** &rarr; **Disconnect All Sessions**
* 
## Services

* **Windows Key + R** &rarr; **services** &rarr; **right click on service** &rarr; properties &rarr; change as applicable

* Bitlocker Drive Encryption Service: **stopped/disabled**
* Bluetooth Support Service: **stopped/disabled**
* DHCP Client: **automatic/running**

	

