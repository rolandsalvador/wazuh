<h1>Wazuh Home Lab</h1>
<a href="https://drive.google.com/file/d/1AOdPrd0vHgvn7jLvgaBpopoZYSuwUPRX/view?usp=sharing">pdf version</a>

<h2>Description</h2>
In this project, I configured Wazuh, a free and open-source SIEM and XDR. I set up four virtual machines to simulate a small network. I used an Ubuntu 22.04 machine to act as the Wazuh server, and then used an Ubuntu 22.04, Windows 10 Pro, and Windows 11 machine to act as the Wazuh agents.

<br />
<br />
<img src="https://i.imgur.com/CcWp3pN.png"/>

After setting everything up, I followed all the example scenarios included in the Wazuh <a href="https://documentation.wazuh.com/4.5/proof-of-concept-guide/index.html">proof of concept documentation</a>. This provided me with great hands-on learning about configuring a SIEM server, setting up rules, and monitoring endpoints. Additionally, I was able to set up integration with third-party tools such as AWS, VirusTotal, Suricata, and Yara. The full list of scenarios I practiced with is provided below.

[1. Blocking a known malicious actor](#1-blocking-a-known-malicious-actor)<br />
[2. File integrity monitoring](#2-file-integrity-monitoring)<br />
[3. Detecting a brute-force attack](#3-detecting-a-brute-force-attack)<br />
[4. Monitoring Docker events](#4-monitoring-docker-events)<br />
[5. Monitoring AWS infrastructure](#5-monitoring-aws-infrastructure)<br />
[6. Detecting unauthorized processes](#6-detecting-unauthorized-processes)<br />
[7. Network IDS integration](#7-network-ids-integration)<br />
[8. Detecting an SQL injection attack](#8-detecting-an-sql-injection-attack)<br />
[9. Detecting suspicious binaries](#9-detecting-suspicious-binaries)<br />
[10. Detecting and removing malware using VirusTotal integration](#10-detecting-and-removing-malware-using-virustotal-integration)<br />
[11. Vulnerability detection](#11-vulnerability-detection)<br />
[12. Detecting malware using Yara integration](#12-detecting-malware-using-yara-integration)<br />
[13. Detecting hidden processes](#13-detecting-hidden-processes)<br />
[14. Monitoring execution of malicious commands](#14-monitoring-execution-of-malicious-commands)<br />
[15. Detecting a Shellshock attack](#15-detecting-a-shellshock-attack)<br />
<br />
I documented my progress with screenshots from the dashboard, showing the relevant events in each scenario. I enjoyed configuring everything and seeing how it all comes together. My next steps in this project are to harden each machine according to CIS benchmark standards and regulatory compliance standards such as NIST 800-53 and PCI DSS. Thank you for taking a look!

<h2>Skills Used</h2>

- SIEM
- XDR
- Linux
- Windows
- Virtualization

<h2>Environments Used</h2>

- Ubuntu 22.04
- Windows 10 Pro
- Windows 11

<h2>Walkthrough</h2>

<h3>1. Blocking a known malicious actor</h3> 
I set up an Apache webserver on the Ubuntu and Windows endpoints. Using another Ubuntu endpoint to act as the attacker, I tried to access the endpoints using the curl command.
<br />
<br />
To demonstrate blocking a known malicious actor, I appended the attacker Ubuntu machine’s IP address to a IP reputation database that I downloaded.
<br />
<br />
Once I tried to curl the endpoint’s Apache server on the attacker machine, it was blocked for 60 seconds.
<br />
<br />
<img src="https://i.imgur.com/1UgWyu9.png"/>
<img src="https://i.imgur.com/EkqN8u7.png"/>

[Back to top](#wazuh-home-lab)
    
<h3>2. File integrity monitoring</h3> 
Wazuh has a built-in file integrity monitoring (FIM) module that tracks the creation, modification, and deletion of files on the endpoints. This helps in auditing important files and meeting compliance standards.
<br />
<br />
To enable FIM on the endpoints, I edited the ossec.conf configuration files to include the /root directory on Ubuntu and Downloads folder on Windows. To confirm it was working, I created, modified, and deleted files in the monitored directories.
<br />
<br />
<img src="https://i.imgur.com/J6s4a3o.png"/>
<img src="https://i.imgur.com/wSEBWUt.png"/>

[Back to top](#wazuh-home-lab)

<h3>3. Detecting a brute-force attack</h3> 
Wazuh detects brute-force attacks automatically by correlating multiple authentication failure events. 
<br />
<br />
To emulate a brute-force attack, I used the Hydra tool on an Ubuntu endpoint. After creating a text file with 10 random passwords, I initiated a brute-force attack on the Ubuntu and Windows endpoints.
<br />
<br />
<img src="https://i.imgur.com/AbPiB8U.png"/>
<img src="https://i.imgur.com/xfxx2hl.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>4. Monitoring Docker events</h3>
Wazuh includes a module to monitor Docker events in real-time. After configuring Docker on the Ubuntu endpoint, I edited the ossec.conf configuration file to enable the “docker-listener” module.
<br />
<br />
As a test, I performed Docker actions like pulling an image, starting an instance, and deleting the container.
<br />
<br />
<img src="https://i.imgur.com/bECeVm2.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>5. Monitoring AWS infrastructure</h3>
Wazuh includes a module for monitoring AWS infrastructure. It analyzes log data stored in an S3 bucket to identify security incidents from different AWS services.
<br />
<br />
After configuring an AWS account, I created a Cloudtrail trail and attached an S3 bucket to it. Then I enabled the AWS module in the ossec.conf configuration file. This required me to configure and add the AWS credentials so that Wazuh had sufficient permissions. 
<br />
<br />
To test, I created and deleted a user once everything was all set up. 
<br />
<br />
<img src="https://i.imgur.com/dtnvu6r.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>6. Detecting unauthorized processes</h3>
Wazuh can periodically get a list of all running processes on the endpoint, which can be configured in the ossec.conf file. 
<br />
<br />
On the Wazuh server, I added a rule in the local_rules.xml file to trigger every time the Netcat program launches.
<br />
<br />
On the Ubuntu endpoint, I ran a Netcat command to trigger an event on the Wazuh dashboard.
<br />
<br />
<img src="https://i.imgur.com/wkKvy60.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>7. Network IDS integration</h3>
In this scenario, I integrated Suricata, a NIDS, with Wazuh. After installing it on the Ubuntu endpoint, I downloaded the Emerging Threats Suricata ruleset and modified settings in the suricata.yaml file. I set the Ubuntu endpoint IP, ruleset path, and the network interface to be monitored. Finally, I edited the ossec.conf file to allow the Wazuh agent to read Suricata log files (eve.json).
<br />
<br />
To emulate an attack, I pinged the Ubuntu endpoint’s IP address from the attacker machine.
<br />
<br />
<img src="https://i.imgur.com/tHHU44s.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>8. Detecting an SQL injection attack</h3>
Making use of the previously setup Apache server on the Ubuntu endpoint, I configured the ossec.conf file to allow the Wazuh agent to monitor the access logs of the Apache server.
<br />
<br />
On the attacker machine, I emulated a SQL injection using the command:
<br />
<i>curl -XGET "http://<UBUNTU_IP>/users/?id=SELECT+*+FROM+users";</i>
<br />
<br />
<img src="https://i.imgur.com/hzH44P5.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>9. Detecting suspicious binaries</h3> 
Wazuh has the ability to detect suspicious binaries on an endpoint. I configured the Ubuntu endpoint’s ossec.conf file to enable the rootcheck module.
<br />
<br />
To emulate a suspicious binary, I created a copy of the original system binary (/usr/bin/w) and replaced it with the following shell script:
<i>
sudo tee /usr/bin/w << EOF
!/bin/bash <br />
echo "`date` this is evil" > /tmp/trojan_created_file <br />
echo 'test for /usr/bin/w trojaned file' >> /tmp/trojan_created_file <br />
Now running original binary <br />
/usr/bin/w.copy <br />
EOF 
</i>
<br />
<br />
<img src="https://i.imgur.com/PAZENv6.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>10. Detecting and removing malware using VirusTotal integration</h3>
Wazuh can integrate with third-party services such as VirusTotal to enhance security capabilities. VirusTotal analyses suspicious files and URLs for malware using antivirus and website scanners.
<br />
<br />
In the Wazuh documentation, they graciously provide active response scripts for Ubuntu and Windows endpoints to remove malicious files. 
<br />
<br />
After adding rules to the Wazuh server’s local_rules.xml file and enabling FIM on the endpoint’s target directories, I downloaded an EICAR test malware files on the endpoints.
<br />
<br />
<img src="https://i.imgur.com/Adqh7nF.png"/>
<img src="https://i.imgur.com/F2QPyBp.png"/>
<img src="https://i.imgur.com/daum4C4.png"/>
<img src="https://i.imgur.com/GEq3ibR.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>11. Vulnerability detection</h3>
After enabling the vulnerability detection module, Wazuh automatically identifies vulnerabilities on the endpoints. Scans are completed periodically for applications and operating systems on the endpoints according to the CVE database.
<br />
<br />
<img src="https://i.imgur.com/N0VBLdD.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>12. Detecting malware using Yara integration</h3>
Yara is another example of a possible integration with Wazuh. In this case, it’s used to detect malware on the Ubuntu and Windows endpoints.
After Yara is installed and configured, the appropriate rules are created on the Wazuh server. 
<br />
<br />
To emulate an attack, I downloaded malware samples that the Wazuh documentation provides through scripts.
<br />
<br />
<img src="https://i.imgur.com/JsybW5e.png"/>
<img src="https://i.imgur.com/UGs8iM0.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>13. Detecting hidden processes</h3>
Wazuh can detect hidden processes. In this scenario, a hidden kernel-mode rootkit is used on an Ubuntu endpoint. Wazuh detects it using setsid(), getpid(), and kill() system calls.
<br />
<br />
After updating the Ubuntu endpoint’s kernel and editing the ossec.conf file to run rootcheck scans every 2 minutes, the Diamorphine rootkit was run on the machine. 
<br />
<br />
Running the kill signal 63 with the PID of a random process unhides the Diamorphine rootkit. Running the kill signal 31 hides or unhides any process, which Wazuh recognizes as an anomaly.
<br />
<br />
<img src="https://i.imgur.com/zojhCcX.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>14. Monitoring execution of malicious commands</h3>
In this scenario, Auditd logs are analyzed by the Wazuh agent for malicious command execution. This can be configured in the ossec.conf file after installing and configuring Auditd.
<br />
<br />
On the Wazuh server, a list of suspicious programs is created and added to the ruleset section in the ossec.conf file. Ncat is set to yellow, nc is set to red, and tcpdump is set to orange. Finally, a rule is created in the local_rules.xml file to activate when a red program is executed.
<br />
<br />
To test the configuration, Netcat, a red program, is installed and run on the Ubuntu endpoint.
<br />
<br />
<img src="https://i.imgur.com/55iOX1I.png"/>

[Back to top](#wazuh-home-lab)
  
<h3>15. Detecting a Shellshock attack</h3>
To detect a Shellshock attack, Wazuh analyzes web server logs collected from an endpoint. I made use of the Apache server on the Ubuntu endpoint again.
<br />
<br />
For the attack emulation, I ran this command from the attacker machine:
<br />
<i>
sudo curl -H "User-Agent: () { :; }; /bin/cat /etc/passwd" (WEBSERVER-IP)
</i>
<br />
<br />
<img src="https://i.imgur.com/AQwKkoU.png"/>
<img src="https://i.imgur.com/AUVVBCI.png"/>

[Back to top](#wazuh-home-lab)
