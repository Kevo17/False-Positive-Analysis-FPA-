<h1>False Positive Analysis (FPA)</h1>


<h2>Description</h2>
This lab focuses on the critical task of False Positive Analysis in the context of security testing and vulnerability scanning. False positives occur when security tools mistakenly identify benign code or configurations as potential security vulnerabilities, leading to unnecessary alarms and wasted resources. False Positive Analysis helps validate and verify the accuracy of security tool findings, ensuring that only genuine security issues are addressed.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Bandit</b>
- <b>JSON</b>

<h2>Environments Used </h2>

- <b>Windows 11</b>
- <b>Linux</b> 

<h2>Program walk-through:</h2>

First, we need to download the source code of the project from our git repository: <br/>
```
git clone https://gitlab.practical-devsecops.training/pdso/dvpa-api
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/e0Fkzub.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s cd into the application so we can scan the app: <br/>
```
cd dvpa-api
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/832JuF9.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s install the bandit scanner on the system to perform static analysis: <br/>
```
pip3 install bandit==1.7.4
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/oPSQJ46.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />


We have successfully installed Bandit scanner. Let’s explore the functionality it provides us: <br/>
```
bandit --help
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/OdVpjcq.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s scan our source code by executing the following command: <br/>
```
bandit -r .
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/iuWZlso.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Analyze the results and mark relevant issues as False Positive & Use Bandit feature to perform False Positive as Code. First we need to modify bandit.baseline.json: <br/>
```
bandit -r . -f json | tee baseline.json
```
```
vi baseline.json
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/a7RVM3x.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
<img src="https://i.imgur.com/YDGPmny.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Delete Not False Positivesand run bandit again: <br/>
```
bandit -r . -f json -o bandit-output.json -b baseline.json
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/sKM7wKn.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />




<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
