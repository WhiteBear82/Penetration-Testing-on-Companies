# Penetration-Testing-on-Companies

## Enumeration
- OSINT
- Nmap
- Web Enumeration

### OSINT

![alt text](https://github.com/WhiteBear82/Penetration-Testing-on-Companies/blob/main/Images/OSINT.jpg?raw=true)<br/>
First step -> What is the target company's name? Google-fu it and see if the company actually owns a publicly facing website. If yes, take a deep dive into the website and dig for information.<br/>
Second step -> What is the target company's name? Google-fu it and look for social media platforms (e.g. Twitter, Facebook, Instagram, LinkedIn) owned by employees working in that company, and take a deep dive into each of these employee's social media platform and note down useful information.<br/>

### Nmap

![alt text](https://github.com/WhiteBear82/Penetration-Testing-on-Companies/blob/main/Images/Enumeration.jpeg?raw=true)<br/>

Syntax 1 -> Aggressive but Informative Nmap Scan. Most commonly used.
> nmap -A -oN results.txt [target-ip-address]

No key? Try Syntax 2 -> Essentially scans for all open ports
> nmap -p- -T5 -oN results.txt [target-ip-address]

<br/>
### Web Enumeration (No login page)

![alt text](https://github.com/WhiteBear82/Penetration-Testing-on-Companies/blob/main/Images/WebEnum.jpg?raw=true)<br/>

1st Attempt -> Always use directory buster (I prefer _dirbuster_ with wordlist _directory-list-2.3-medium.txt_) -> Reveals interesting folders/files<br/>
2nd Attempt -> Always read all source pages (I typically focus on _comments_) -> Reveals interesting comments that gives additional website information<br/>
3rd Attempt -> Use Burp Suite to intercept and capture requests to check interesting information being forwarded and received<br/>

### Web Enumeration (Login page)

![alt text](https://github.com/WhiteBear82/Penetration-Testing-on-Companies/blob/main/Images/WebLogin.jpg?raw=true)<br/>

1st Attempt -> Try common credentials such as (admin:admin), (guest:guest), (admin:password), (root:password), (root:root)<br/>
2nd Attempt -> Try known credentials that was obtained through OSINT, from other machines, etc.<br/>
3rd Attempt -> Brute force into the website login page<br/>
> hydra -L [user list file] -P [password list file] [target-ip-address] http-post-form "[Login Page]:[Request Body]:[Error Message]"<br/>
