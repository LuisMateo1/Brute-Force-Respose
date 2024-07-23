# Brute Force Response

This is the alert on the SIEM
![image](https://github.com/user-attachments/assets/2c4661d8-e555-4eb8-95ae-a07c0db76069)

First I'll investigate the malicious IP on the threat intelligence tab. The IP is listed as malicious
![image](https://github.com/user-attachments/assets/dcdd3fa9-569a-4bf1-88e3-eedb0b74e58f)

I also checked on AbuseIPDB and Cisco Talos and the IP has been reported and is listed on three block lists 

![image](https://github.com/user-attachments/assets/58e634cb-861a-4bf4-a6cd-068e0a9ef520)
![image](https://github.com/user-attachments/assets/406737e5-0b8c-4290-af3a-c1010e94b998)

After checking the event logs, the attacker tried to log on with a few credentials: admin, guest, sysadmin, and Matthew (the user of this workstation). 
![image](https://github.com/user-attachments/assets/c72eb7b0-56e1-4de6-af6a-7b83b034b561)
Also based on the logs the attacker only attempted to RDP to this machine.

Here we see an outlier, EventID 4624: Successful log-on, @ 11:44 AM. Any activity after this time should be investigated and this is enough evidence to contain the workstation
![image](https://github.com/user-attachments/assets/38ed16f7-3e41-49e6-becd-a3fcc00c98ee)
![image](https://github.com/user-attachments/assets/1e5e8b59-d87f-4c44-8de4-c2019e8999ba)
![image](https://github.com/user-attachments/assets/b5f1673e-9955-461d-bffd-e6ffcf4f48e6)

Checking the network logs there was information sent to the malicious IP @ 11:44 AM
![image](https://github.com/user-attachments/assets/0a0afcd8-1085-44bd-8989-2135a30fc578)

@ 11:45 AM the attacker runs a few commands, likely looking for a way to escalate privileges
![image](https://github.com/user-attachments/assets/e200314d-deb5-4970-9867-3281e1e2cbb4)

With the machine quarantined all thats left is to block the IP and close out the ticket
![image](https://github.com/user-attachments/assets/e8afacbf-cced-47d4-a337-9d6c4e21becf)
