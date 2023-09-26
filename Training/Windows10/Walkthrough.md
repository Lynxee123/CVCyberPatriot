# Windows 10 Training Round Image

## Forensic's Questions: 16 Points

#### Forensics Question 1: 8 Points

```
You intercepted a secret message meant for mmayfield and you need to decode it.  
The message is: **52756e6e696e6720557020546861742048696c6c**

What is the decoded message meant for mmayfield?

( EXAMPLE: I see you now )

ANSWER: <Type Answer Here>
```
At first glance, with prior knowledge, you can see that this message is encoded in Hexidecimal Bytes. In order to decode this, we can use an online hexadecimal to ASCII converter :
[cryptii.com](https://cryptii.com)

![cryptii screenshot](./photos/cryptii.png)


#### Forensics Question 2: 8 Points

```
Hash functions are one way functions. Secure hash functions have several 
properties such as collision resistance, preimage resistance, and second 
preimage resistance. Hashes are the output of hash functions and are typically
displayed to the user in hex.

What is the RIPEMD-160 hash of the file in your Pictures directory named 
"nina.jpg"?

( EXAMPLE: DF5C241505DBFBB04DEC0F3A1EB9489F32903154 )

ANSWER: <Type Answer Here>
```

What we need: 
* **RIPEMD-160 hash generator**
* **file path**
*  **hope**

Luckily, powershell has a built in RIPEMD-160 hash generator, thanks to the Get-FileHash function!

```
Get-FileHash -Algorithm RIPEMD160 C:\Users\eleven\Pictures\nina.jpg
```

![powershell screenshot](./photos/powershell.png)

With this function we can specify the algorithm with the -Algorithm tag, allowing us to get a hash with any of these algorithms:
* MD5 (Insecure)
* SHA1 (Slightly Insecure)
* SHA256
* SHA384
* SHA512
* RIPEMD-160 (deprecated)

## Windows Update: 5 Points

#### Majority of Windows Updates Installed: 5 Points

* **Windows Key &rarr; Settings &rarr; Update and Security &rarr; Check for Updates &rarr; Download**

The settings window can be closed as the updates are ran through a service.

## Disabling/Enabling Services: 14 Points

#### Firewall Enabled: 4 Points

* **Windows Key &rarr; Windows Security &rarr; Firewall and Network Protection &rarr; Turn On &rarr; Yes**  

Enabling your firewall is key to helping prevent malicious attacks and attempts at breaking into your network.

#### Remote Assistance Disabled: 5 Points

* **Windows Key + R &rarr; control &rarr; System &rarr; Remote Settings &rarr; Allow Remote Assistance Connections to This Computer &rarr; Uncheck the Box &rarr; OK**

Ever watched scam callers remote "assist" people into giving them bank information? Don't enable it.

#### FTP Service Stopped and Disabled: 5 Points

* **Windows Key + R &rarr; services.msc &rarr; Scroll Down to Microsoft FTP Service &rarr; Double Click &rarr; Startup Type: Disabled &rarr; Stop Service &rarr; OK**

FTP (File Transfer Protocol), runs off of port 21 and is known to cause issues when it comes to unwanted users enumerating your file system/watching your plaintext data stream. Disable FTP unless you are using a file server through a vpn or SFTP tunnel (Secure FTP - Encrypted Connection)

## Updating Applications: 8 Points

Ensuring apps are up to date is good for preventing possible outdated software vulnerabilites. You should almost always get points for updating required applications (check the readme).

#### Update Tiled: 4 Points

* **Open Tiled &rarr; Help (upper left corner) &rarr; About Tiled &rarr; Update Available &rarr; Download &rarr; No Thanks, just take me to the downloads &rarr; Windows 10+ (64-bit) &rarr; Run the installer**

#### Update Firefox: 4 Points

* **Open Firefox &rarr; Click ? on the Help Menu &rarr; About Firefox &rarr; Check for Updates &rarr; Update to (version) &rarr; Restart to Update Firefox**

## Remove Hacking Tools and Malware: 12 Points

#### Remove Wireshark: 4 Points

* **Windows Key + R &rarr; control &rarr; Programs &rarr; Programs and Features &rarr; Wireshark &rarr; Uninstall &rarr; follow the uninstall prompts**

Wireshark is a tool for scanning network packets. Sometimes you may need hacking tools to solve forensics questions, but upon completing the question and getting points you should delete them (**unless stated otherwise in the readme**)

#### Remove NetStumbler: 4 Points

* **Windows Key + R &rarr; control &rarr; Programs &rarr; Programs and Features &rarr; Network Stumbler 0.4.0 &rarr; Uninstall &rarr; follow the uninstall prompts**

NetStumbler is a tool for detecting Wireless networks in your area. Hacking tools like these can increase your computers attack surface due to the open ports they require to run on, as well as presenting many legal and regulatory issues for your company.

#### Remove PC Cleaner: 4 Points

* **Windows Key + R &rarr; control &rarr; Programs &rarr; Programs and Features &rarr; PC Cleaner v9.0.0.9 &rarr; Uninstall &rarr; follow the uninstall prompts**

## Users and Groups: 23+ Points

Check the Readme while windows is downloading updates to find a list of authorized user accounts. Any user account you see in the lusrmgr.msc management console that is not on that list must be deleted, as well as removing authorized users from any groups they are not authorized to be in (Such as unauthorized administrators). Also check for any groups that are authorized, and determine if they need to be created or not.

#### Removed User pmckinney: 3 Points

* **Windows Key + R &rarr; lusrmgr.msc &rarr; Users &rarr; right click pmckinney &rarr; Delete &rarr; Yes**


#### Removed User yismaylov: 3 Points

* **Windows Key + R &rarr; lusrmgr.msc &rarr; Users &rarr; right click yismaylov &rarr; Delete &rarr; Yes**

#### User jbyers Removed from Admininstrator Group: 3 Points

* **Windows Key + R &rarr; lusrmgr.msc &rarr; Groups &rarr; Double Click Administrators &rarr; jbyers &rarr; Remove &rarr; OK**

#### User mbauman Removed from Admininstrator Group: 3 Points

* **Windows Key + R &rarr; lusrmgr.msc &rarr; Groups &rarr; Double Click Administrators &rarr; mbauman &rarr; Remove &rarr; OK**

#### Set a Password for argyle: 3 Points

* **Windows Key + R &rarr; lusrmgr.msc &rarr; Users &rarr; right click argyle &rarr; Set Password &rarr; Enter P@$$word12345679 into both boxes &rarr; Confirm**

#### Create User esinclair: 4 Points

* **Windows Key + R &rarr; lusrmgr.msc &rarr; Users &rarr; Action &rarr; New Users &rarr; esinclair (username and full name) &rarr; P@$$word123456789 &rarr; Create &rarr; Close**

#### Create Group dragonfire - Add Users: 4 Points Each

* **Windows Key + R &rarr; lusrmgr.msc &rarr; Groups &rarr; Action &rarr; New Group &rarr; dragonfire &rarr; add &rarr; enter usernames specified in readme (seperated by semicolons) &rarr; OK &rarr; Create &rarr; Close**

## Security Policies: 18 Points

#### Secure Maximum Password Age: 4 Points

* **Windows Key + R &rarr; secpol.msc &rarr; Security Settings &rarr; Account Policies &rarr; Password Policy &rarr; Maximum Password Age: 90 days &rarr; OK**

#### Secure Lockout Threshold: 4 Points

* **Windows Key + R &rarr; secpol.msc &rarr; Security Settings &rarr; Account Policies &rarr; Account Lockout Policies &rarr; Account Lockout Threshold: 10 invalid login attempts &rarr; OK**

#### Limit Local Use of Blank Passwords to Console Only Enabled: 5 Points

* **Windows Key + R &rarr; secpol.msc &rarr; Security Settings &rarr; Local Policies &rarr; Security Options &rarr; Acounts: Limit local use of blank passwords to console only: Enabled &rarr; OK**

#### Do not allow anonymous enumeration of SAM accounts Enabled: 5 Points

* **Windows Key + R &rarr; secpol.msc &rarr; Security Settings &rarr; Local Policies &rarr; Network access: do not allow anonymous enumeration of SAM accounts: Enabled &rarr; OK**