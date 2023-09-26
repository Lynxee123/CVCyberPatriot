# Ubuntu 22 Training Round

You should run the following command to become root and have less restrictions:
```bash
$ sudo -i
```

## Forensics Questions

### Forensics Question 1

> Points: 8

```
Major Monogram, your commanding officer, left a mission for you on your Desktop.
( /home/perry/Desktop/mission.txt )

Because this mission is for your eyes only, it has been encoded.

What type of legal document did Major Monogram tell you has been signed?

( EXAMPLE: contract )

ANSWER: <Type Answer Here>
```

The content of `/home/perry/Desktop/mission.txt` is:
```
QWdlbnQgUCwgDQoNCkRvb2ZlbnNobWlydHogY2xhaW1zIHRvIGhhdmUgZ2l2ZW4gdXAgZXZpbC4gSGUgZXZlbiBzaWduZWQgdGhpcyDigJxJIEdpdmUgVXAgRXZpbOKAnSBhZmZpZGF2aXQgdG8gYXBwbHkgZm9yIHdvcmsgYXQgdGhlIGFnZW5jeS4gDQpXZeKAmXJlIG1ha2luZyBEb29mZW5zaG1pcnR6IHlvdXIgcmVzcG9uc2liaWxpdHkgZHVyaW5nIGhpcyBwcm9iYXRpb24gcGVyaW9kLiANClNob3cgaGltIHRoZSByb3BlcywgYW5kIGRvbuKAmXQgbGV0IGhpbSBvdXQgb2YgeW91ciBzaWdodC4NCg0KTW9ub2dyYW0gb3V0IQ==
```

This data looks like base64 data, so you decode:

```bash
$ echo "QWdlbnQgUCwgDQoNCkRvb2ZlbnNobWlydHogY2xhaW1zIHRvIGhhdmUgZ2l2ZW4gdXAgZXZpbC4gSGUgZXZlbiBzaWduZWQgdGhpcyDigJxJIEdpdmUgVXAgRXZpbOKAnSBhZmZpZGF2aXQgdG8gYXBwbHkgZm9yIHdvcmsgYXQgdGhlIGFnZW5jeS4gDQpXZeKAmXJlIG1ha2luZyBEb29mZW5zaG1pcnR6IHlvdXIgcmVzcG9uc2liaWxpdHkgZHVyaW5nIGhpcyBwcm9iYXRpb24gcGVyaW9kLiANClNob3cgaGltIHRoZSByb3BlcywgYW5kIGRvbuKAmXQgbGV0IGhpbSBvdXQgb2YgeW91ciBzaWdodC4NCg0KTW9ub2dyYW0gb3V0IQ==" | base64 -d

Agent P, 

Doofenshmirtz claims to have given up evil. He even signed this “I Give Up Evil” affidavit to apply for work at the agency. 
We’re making Doofenshmirtz your responsibility during his probation period. 
Show him the ropes, and don’t let him out of your sight.

Monogram out!
```

This says that he signed an affidavit, so the answer will be "affidavit".

### Forensics Question 2

> Points: 8

```
There are prohibited MP3 files somewhere on this computer that are not work 
related.

What is the absolute path of the directory containing the prohibited MP3 files?

( EXAMPLE: /home/perry/Downloads )

ANSWER: <Type Answer Here>
```

You need to find specific file types, so you run the following command:

```bash
$ locate '*.mp3'

'/home/linda/Music/Ain'$'\'''t Got Rhythm.mp3'
'/home/linda/Music/Couldn'$'\'''t Kick My Way Right Into Her Heart.mp3'
/home/linda/Music/Fabulous.mp3
/home/linda/Music/You Snuck Your Way Right Into My Heart.mp3
```

The audio files are all in the `/home/linda/Music` folder.

## Remove unauthorized users

> Points: 6

### Removed unauthorized user balloony

> Points: 6

`balloony` is not in the list of allowed users in the README.

To remove the user you can run the following command:

```bash
$ deluser balloony
```

# Remove unauthorized administrators

> Points: 12

### User doofenshmirtz is not an administrator

> Points: 6

`doofenshmirtz` is designated as an administrator (is in sudo group), but is not in the allowed administrators in the README

There are a couple of ways to remove the user from being an administrator:

 - Run `$ deluser doofenshmirtz sudo`

 - Open Settings &rarr; Users, click `Unlock` at the top, select the `doofenshmirtz` user, and toggle off `Administrator`

### User lawrence is not an administrator

> Points: 6

`lawrence` is designated as an administrator (is in sudo group), but is not in the allowed administrators in the README

There are a couple of ways to remove the user from being an administrator:

 - Run `$ deluser lawrence sudo`

 - Open Settings &rarr; Users, click `Unlock` at the top, select the `lawrence` user, and toggle off `Administrator`

## Change insecure passwords

> Points: 6

### Changed insecure password for user pinky

> Points: 6

The password set for `pinky` is insecure (grilledcheese).

There are a couple of ways to change their password:

 - Run `$ passwd pinky` then enter a new *secure* password

 - Open Settings &rarr; Users, click `Unlock` at the top, click `Password`, and set a new password.

You should note this password in a document so you can still access the account.

## Disable services

> Points: 6

### Nginx service has been disabled or removed

> Points: 6

The README doesn't specify the `nginx` service as a required service, so it should be disabled.

To check for running services use the command:

```bash
$ systemctl list-units --type=service --state=active
```

To disable the `nginx` service use the command:

```bash
$ systemctl stop nginx
$ systemctl disable nginx
```

To remove the `nginx` package from the system:

```bash
$ apt purge nginx
```

## Update applications

> Points: 10

### Firefox has been updated

> Points: 5

To update Firefox you can run the following command:

```bash
$ apt update
$ apt upgrade
```

### Thunderbird has been updated

> Points: 5

To update Thunderbird you can use the command:

```bash
$ apt update
$ apt upgrade
```

## Remove prohibited software and files

> Points: 18

### Prohibited MP3 files are removed

> Points: 6

To find the MP3 files use the command:

```bash
$ locate '*.mp3'
```

To remove the files use the command:

```bash
$ rm /home/linda/Music/*.mp3
```

### Prohibited software ophcrack removed

> Points: 6

Third-party software should be limited to software specified in the README

To remove the ophcrack package use the following command:

```bash
$ apt remove ophcrack
```

### Prohibited software Wireshark removed

> Points: 6

Third-party software should be limited to software specified in the README

To remove the wireshark package use the following command:

```bash
$ apt remove wireshark
```

## Security

> Points: 18

### Uncomplicated Firewall (UFW) protection has been enabled

> Points: 6

To determine if UFW is disabled run the command:
```bash
$ ufw status

Status: inactive
```

You can run the following command to enable the firewall:
```bash
$ ufw enable

Firewall is active and enabled on system startup

### SSH root login has been disabled

> Points: 6

Use the following command to open the ssh config:

```bash
$ nano /etc/ssh/sshd_config
```

Change the line `PermitRootLogin yes` to `PermitRootLogin no`

Press ^X, Y, Enter to save and exit.

### The system automatically checks for updates daily

> Points: 6

You can solve this problem by doing the following:

Software & Updates &rarr; Updates &rarr; Automatically check for updates, and select `Daily`

## Other

> Points: 8

### Added candace to group firesidegirls

> Points: 8

The README requests that you add `candace` to the `firesidegirls` group.

You can run the following command to add `candace` to `firesidegirls`:

```bash
$ usermod -aG firesidegirls candace
```

## Penalties

### OpenSSH service has been stopped or removed

> Points: -5

OpenSSH is a critical service according to the README.

To reinstall openssh use the following command:

```bash
$ apt install openssh
```

### Firefox has been removed

> Points: -5

Firefox is required software according to the README.

To reinstall firefox use the following command:

```bash
$ apt install firefox
```

### Thunderbird has been removed

> Points: -5

Thunderbird is required software according to the README.

To reinstall thunderbird use the following command:

```bash
$ apt install thunderbird
```

### Perl has been removed

> Points: -5

Perl is required software according to the README.

To reinstall perl use the following command:

```bash
$ apt install perl
```