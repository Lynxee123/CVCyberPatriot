# Ubuntu 22 Training Round

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

You need to find specific file types, so you run the following command

```bash
$ locate .mp3

'/home/linda/Music/Ain'$'\'''t Got Rhythm.mp3'
'/home/linda/Music/Couldn'$'\'''t Kick My Way Right Into Her Heart.mp3'
/home/linda/Music/Fabulous.mp3
/home/linda/Music/You Snuck Your Way Right Into My Heart.mp3
```

The audio files are all in the `/home/linda/Music` folder.