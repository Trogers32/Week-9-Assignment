# Week-9-Assignment

## _Honeypots used:_

##### I started off with these: 
- Dionaea - "meant to be a nepenthes successor, embedding python as scripting language, using libemu to detect shellcodes, supporting ipv6 and tls."

- ElasticHoney -a "simple elasticsearch honeypot designed to catch attackers exploiting RCE vulnerabilities in elasticsearch."

- Wordpot - a "Wordpress honeypot which detects probes for plugins, themes, timthumb and other common files used to fingerprint a Wordpress installation."

- Cowrie - a "medium interaction SSH and Telnet honeypot designed to log brute force attacks and the shell interaction performed by the attacker."

##### When I didn't get many hits I moved on to more sensitive pots:
- p0f -a "tool that utilizes an array of sophisticated, purely passive traffic fingerprinting mechanisms to identify the players behind any incidental TCP/IP communications (often as little as a single normal SYN) without interfering in any way."

- Suricata -"capable of real time intrusion detection (IDS), inline intrusion prevention (IPS), network security monitoring (NSM) and offline pcap processing."

## Issues:

- The firewall rule script did not include a "-1" at the end of it, which would mark the mhn-honeypot-1 as one of the target tags.
  - Initially thought that my normal computer firewall was blocking the traffic until looking further into the firewall rules on the GCD website.

- The wget command to execute the script to install the desired honeypot was using an unreachable IP address. Upon executing the command the script would hang until it timed out and would automatically retry the connection. Corrected this by using the mhn-admin IP address.

- Hours spent trying to download the json file from the vm instance: 6
  - Tried searching for different ways to download or transfer the files on the google cloud platform.
  - Tried downloading WinSCP and adding it to the Environment Variable PATH.
  - Tried separate file names and possible database and collection names.
  - Spent time looking through the structure of the mhn-admin vm directory and testing to see if the commands were passing through the correct path.
  - **The correct commands are:** 
    - mongoexport --db mnemosyne --collection session > session.json
      - This had to be done within the "gcloud compute ssh mhn-admin"
    - gcloud compute scp mhn-admin:./session.json ./session.json 
    - The only change that was necessary from the original instruction was to change the '~' before /session to a '.'

## Summary of the data collected:

**Collection started at 1630 on 30 November, 2018.**
**Collection ended at 1930 on 1 December, 2018**

- Dionaea
  - Number of Attacks: 26
  - US West Server
  - Dst port 3389 // Protocol pcap

- ElasticHoney
  - Number of Attacks: 0
  - US West Server

- Wordpot
  - Number of Attacks: 0
  - US West Server

- Cowrie
  - Number of Attacks: 23
  - US East Server
  - Dst port 22 // Protocol ssh

- p0f
  - Number of Attacks: 3413
  - US East Server
  - Dst port 22 // Protocol pcap
  
 - Suricata
   - Number of Attacks: 1855
   - Europe North Server
   - DST port 80 // Protocol TCP
   - Dst port 22 // Protocol TCP
   - Payloads: 
     - Continous hits from an IP address that leads back to Linode, LLC.
       - Appears to be a Python script that is meant for logging.
       - Signature: "ET POLICY Python-urllib/ Suspicious User Agent"
     - ET SCAN LibSSH Based Frequent SSH Connections Likely BruteForce Attack
     - ET SCAN Potential SSH Scan
     - ET COMPROMISED Known Compromised or Hostile Host Traffic TCP group 4

### Unresolved questions:
 - What was the Python logging script for?
