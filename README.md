<h1>Wazuh Home Lab</h1>

<h2>Description</h2>
In this project, I configured Wazuh, a free and open-source SIEM and XDR. I set up four virtual machines to simulate a small network. I used an Ubuntu 22.04 machine to act as the Wazuh server, and then used an Ubuntu 22.04, Windows 10 Pro, and Windows 11 machine to act as the Wazuh agents.

<br />
<br />
<p align="center">
<img src="https://i.imgur.com/CcWp3pN.png" height="80%" width="80%"/>

After setting everything up, I followed all the example scenarios included in the Wazuh <a href="https://documentation.wazuh.com/4.5/proof-of-concept-guide/index.html">proof of concept documentation</a>. This provided me with great hands-on learning about configuring a SIEM server, setting up rules, and monitoring endpoints. Additionally, I was able to set up integration with third-party tools such as AWS, VirusTotal, Suricata, and Yara. The full list of scenarios I practiced with is provided below.

<br />
<p align="center">
<img src="https://i.imgur.com/dijTHH4.png" height="50%" width="50%"/>

I documented my progress with screenshots from the dashboard, showing the relevant events in each scenario. I enjoyed configuring everything and seeing how it all comes together. My next steps in this project are to harden each machine according to CIS benchmark standards and regulatory compliance standards such as NIST 800-53 and PCI DSS. Thank you for taking a look!

<h2>Skills Used</h2>

- SIEM
- XDR
- Linux
- Windows
- Virtualization

<h2>Environments Used </h2>

- Ubuntu 22.04
- Windows 10 Pro
- Windows 11

<h2>Walkthrough</h2>
1. <b> Blocking a known malicious actor </b> 
  <br /> <br />
2. <b> File integrity monitoring </b> 
  <br /> <br />
3. <b> Detecting a brute-force attack </b> 
  <br /> <br />
4. <b> Monitoring Docker events </b> 
  <br /> <br />
5. <b> Monitoring AWS infrastructure </b> 
  <br /> <br />
6. <b> Detecting unauthorized processes </b> 
  <br /> <br />
7. <b> Network IDS integration </b> 
  <br /> <br />
8. <b> Detecting an SQL injection attack </b> 
  <br /> <br />
9. <b> Detecting suspicious binaries </b> 
  <br /> <br />
10. <b> Detecting and removing malware using VirusTotal integration </b> 
  <br /> <br />
11. <b> Vulnerability detection </b> 
  <br /> <br />
12. <b> Detecting malware using Yara integration </b> 
  <br /> <br />
13. <b> Detecting hidden processes </b> 
  <br /> <br />
14. <b> Monitoring execution of malicious commands </b> 
  <br /> <br />
15. <b> Detecting a Shellshock attack </b> 
  <br /> <br />

<!--

<br />
<br />
<p align="center">
<img src="" height="80%" width="80%"/>


<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
--!>
