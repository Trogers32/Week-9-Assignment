# Week-9-Assignment

## Honeypots used:

- Dionaea - "meant to be a nepenthes successor, embedding python as scripting language, using libemu to detect shellcodes, supporting ipv6 and tls."

- ElasticHoney -a "simple elasticsearch honeypot designed to catch attackers exploiting RCE vulnerabilities in elasticsearch."

- Wordpot - a "Wordpress honeypot which detects probes for plugins, themes, timthumb and other common files used to fingerprint a Wordpress installation."

- Cowrie - a "medium interaction SSH and Telnet honeypot designed to log brute force attacks and the shell interaction performed by the attacker."

- p0f -a "tool that utilizes an array of sophisticated, purely passive traffic fingerprinting mechanisms to identify the players behind any incidental TCP/IP communications (often as little as a single normal SYN) without interfering in any way."

- Suricata -"capable of real time intrusion detection (IDS), inline intrusion prevention (IPS), network security monitoring (NSM) and offline pcap processing."

## Issues:

- The firewall rule script did not include a "-1" at the end of it, which would mark the mhn-honeypot-1 as one of the target tags.
  - Initially thought that my normal computer firewall was blocking the traffic until looking further into the firewall rules on the GCD website.

- The wget command to execute the script to install the desired honeypot was using an unreachable IP address. Upon executing the command the script would hang until it timed out and would automatically retry the connection. Corrected this by using the mhn-admin IP address.

## Summary of the data collected:

**Collection started at 1630 on 30 November, 2018.**

- Dionaea
  - Number of Attacks: 
  - US West Server
  - Dst port 3389 // Protocol pcap
  - Src countries: Russia, Taiwan, Seychelles, Netherlands, Ukraine

- ElasticHoney
  - Number of Attacks: 
  - US West Server

- Wordpot
  - Number of Attacks: 
  - US West Server

- Cowrie
  - Number of Attacks: 
  - US East Server
  - Dst port 22 // Protocol ssh
  - Src countries: China, Vietnam, USA, France

- p0f
  - Number of Attacks: 
  - US East Server
  - Dst port 22 // Protocol pcap
  - Src countries: Many
  - This was the Honeypot that received the most hits with a total of
  
 - Suricata
  - # of Attacks:
  - Europe North Server
  - DST port 80 // Protocol TCP
  - Continous hits from an IP address that leads back to Linode, LLC.

### Unresolved questions:
