---
title: Technical Walkthrough on Sapphire Stealer 
date: 2023-10-31 10:00
categories: [security, malware]
tags: [malware, sapphire, stealer]

---


SapphireStealer is an open-source information stealer that was first released on GitHub in December 2022. It is a relatively new malware, but it has quickly become popular among threat actors. It is designed to steal sensitive information from infected devices, such as - Browser credentials, File contents, Screenshots, System information etc. The malware can also steal cryptocurrency wallets and other sensitive data. 

SapphireStealer is typically spread through phishing emails and malicious attachments. Once it is installed on a device, it can steal data without the user's knowledge.SapphireStealer’s codebase was published on [GitHub](https://github.com/0day2/SapphireStealer/) on Dec. 25, 2022.

Threat actors quickly began experimenting with the open-source malware codebase for SapphireStealer after its release. They added new features and used other tools to make it harder to detect SapphireStealer infections. New versions of SapphireStealer were uploaded to public malware repositories starting in mid-January 2023, and this continued for the first half of the year. The compilation artifacts associated with these samples show that multiple threat actors are using this malware codebase. There are already many different versions of SapphireStealer in the wild, and threat actors are making it more efficient and effective over time.

This stealer performs few actions of creating files and folder inside `temp` directory . Initially, it creates  a folder called `sapex` and later it creates another folder inside sapex called `GrabbingFiles`. Further, a file named `passwords.txt` is created inside sapex folder which is used later.


Secondly,it performs browser stealing activities which extracts user information such as Passwords and username and website from it and save it in `passwords.txt` file. the sample which we are referencing was modified to query browser data which belongs to Chrome. 
![First Image](https://github.com/SaiKrishnaKarnati/SaiKrishnaKarnati.github.io/blob/main/assets/sapphire/1.png?raw=true)

However, Code published on github searches for all Browsers hardcoded with their paths. If these paths exists, then it will extract  user information and save it in a log file.
![Second Image](https://github.com/SaiKrishnaKarnati/SaiKrishnaKarnati.github.io/blob/main/assets/sapphire/2.png?raw=true)

Apart form that , it grabs files from desktop which has file extensions such as `pdf` and `doc` and save all these files inside `Grabbingfiles` directory which is created before inside `temp` directory. Later, it takes screenshot of Desktop and saves it in `sapex` directory.
![Third Image](https://github.com/SaiKrishnaKarnati/SaiKrishnaKarnati.github.io/blob/main/assets/sapphire/3.png?raw=true)

After performing all these actions, these data are zipped with `cp866` encoding and saved it in temp directory with the name `log.zip`.
![Fourth Image](https://github.com/SaiKrishnaKarnati/SaiKrishnaKarnati.github.io/blob/main/assets/sapphire/4.png?raw=true)

Further, it starts querying for information such as Hostname, Ipaddress, Username, OSVersion, HWID, GPUName All these information sent inside a message body via mail over SMTP .
![Fifth Image](https://github.com/SaiKrishnaKarnati/SaiKrishnaKarnati.github.io/blob/main/assets/sapphire/5.png?raw=true)


Finally, it deletes the folder `sapex` inside temp folder after performing all above activities.