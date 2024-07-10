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

<h2>Environments Used</h2>

- Ubuntu 22.04
- Windows 10 Pro
- Windows 11

<h2>Walkthrough</h2>

<h3>1. Blocking a known malicious actor</h3> 
<p align="center">
<img src="https://i.imgur.com/1UgWyu9.png"/>
<p align="center">
<img src="https://i.imgur.com/EkqN8u7.png"/>
    
<h3>2. File integrity monitoring</h3> 
<p align="center">
<img src="https://i.imgur.com/J6s4a3o.png"/>
<p align="center">
<img src="https://i.imgur.com/wSEBWUt.png"/>

<h3>3. Detecting a brute-force attack </h3> 
<p align="center">
<img src="https://i.imgur.com/AbPiB8U.png"/>
<p align="center">
<img src="https://i.imgur.com/xfxx2hl.png"/>
  
<h3>4. Monitoring Docker events</h3>
<p align="center">
<img src="https://i.imgur.com/bECeVm2.png"/>
  
<h3>5. Monitoring AWS infrastructure</h3>
<p align="center">
<img src="https://i.imgur.com/dtnvu6r.png"/>
  
<h3>6. Detecting unauthorized processes</h3>
<p align="center">
<img src="https://i.imgur.com/wkKvy60.png"/>
  
<h3>7. Network IDS integration</h3>
<p align="center">
<img src="https://i.imgur.com/tHHU44s.png"/>
  
<h3>8. Detecting an SQL injection attack</h3>
<p align="center">
<img src="https://i.imgur.com/hzH44P5.png"/>
  
<h3>9. Detecting suspicious binaries</h3> 
<p align="center">
<img src="https://i.imgur.com/PAZENv6.png"/>
  
<h3>10. Detecting and removing malware using VirusTotal integration</h3>
<p align="center">
<img src="https://i.imgur.com/Adqh7nF.png"/>
<p align="center">
<img src="https://i.imgur.com/F2QPyBp.png"/>
<p align="center">
<img src="https://i.imgur.com/daum4C4.png"/>
<p align="center">
<img src="https://i.imgur.com/GEq3ibR.png"/>
  
<h3>11. Vulnerability detection</h3>
<p align="center">
<img src="https://i.imgur.com/N0VBLdD.png"/>
  
<h3>12. Detecting malware using Yara integration</h3>
<p align="center">
<img src="https://i.imgur.com/JsybW5e.png"/>
<p align="center">
<img src="https://i.imgur.com/UGs8iM0.png"/>
  
<h3>13. Detecting hidden processes</h3>
<p align="center">
<img src="https://i.imgur.com/zojhCcX.png"/>
  
<h3>14. Monitoring execution of malicious commands</h3>
<p align="center">
<img src="https://i.imgur.com/55iOX1I.png"/>
  
<h3>15. Detecting a Shellshock attack</h3>
<p align="center">
<img src="https://i.imgur.com/AQwKkoU.png"/>
<p align="center">
<img src="https://i.imgur.com/AUVVBCI.png"/>

<!--

<br />
<br />
<p align="center">
<img src="" height="80%" width="80%"/>

<p align="center">
<img src=""/>

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
