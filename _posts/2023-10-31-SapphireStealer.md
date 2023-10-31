---
title: Technical Walkthrough on Sapphire Stealer 
date: 2023-10-31 10:00
categories: [security, malware]
tags: [malware, sapphire, stealer]

---




### Wannacry Analysis
Wannacry is a self propogating malware which is classified as crypto-ransomware afftecting more than 200K computers in 2017. A Crypto ransomware is a harmful computer program that encrypts user's files for money extortion purpoeses(Ransom). This malware has worm capaibility which can propogate to other computers through computer networks.

Wannacry malware exploits the vulnerability that is in Server message Block(SMB) Protocol of the windows implementation. SMB is a Transport protocol used for file sharing , printer sharing and remote services in windows. This protocol operates over TCP port 445 and 139. The malware makes use of SMBv1 and TCP port 445 to propogate. This vulnerability allows malformed packets from the remote attackers to execute arbitary code on the victims computer.

Let's discuss about few **Terminologies** to understand before execution:-