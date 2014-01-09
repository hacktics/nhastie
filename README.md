<article>

<h1>NHASTIE</H1>
<h2>NTLM HTTP Authentication Session Tier Exploit</h2>

<p>NHASTIE is a lightweight Proof of Concept tool that <b>exploits NTLM HTTP authentication in web applications</b>. Once a victim issues an HTTP request to this tool, the attacker can connect to NHASTIE and <b>surf the vulnerable NTLM HTTP web application using the victim's identity!</b></p>

<p>Developed by <a href="https://twitter.com/oren1ofer">Oren Ofer</a> of <a href="http://www.hacktics.com" target="_blank">Hacktics ASC</a><br>
<a href="http://www.hacktics.com" target="_blank"><img src="http://diviner.googlecode.com/files/hacktics_logo.jpg" /></a></p>

<hr/>

<p>
<h2>Requirements:</h2>
<ul>
<li> NHASTIE requires Java <u>1.7.x</u></li>
</ul>
</p>

<p><h2>How Does it Work?</h2>
NTLM HTTP authentication is based on a TCP connection, i.e. the connection is the session (I call it "ConSessions"). In order to exploit this fact here is what NHASTIE does:
<ol>
<li> The tool creates a single TCP socket which will be used to transfer all communication to and from the target web application, and stands by (listening) for a victim.</li>
<li> A victim issues an HTTP request to the tool and the tool forwards the HTTP request to the designated web application.</li>
<li> The Web application replies with a demand to authenticate using NTLM, the tool forwards the response to the victim.</li>
<li> The victim automatically responds with a valid NTLM authentication, which is forwarded by the tool the web application by the same TCP socket.</li>
<li> The web application treats all future incoming HTTP requests from this TCP socket as authenticated by the victim.</li>
<li> The attacker connects to the tool using a browser, and surfs the vulnerable web application using the victim's identity!</li>
</ol>
</p>

<p><h2>Can Attackers Make Victims Connect to this Tool?</h2>
Yes, and in numerous ways, for example:
<ol>
<li> Asking - Be nice :)</li>
<li> Phishing - Luring users to use a link HTTP/UNC/SMB</li>
<li> Open of template based word, a .lnk file or access a share with desktop.ini file</li>
<li> Using web application attacks - XSS, CSRF, etc.</li>
<li> Forcing with MITM</li>
</ol>
Several instances that will trigger NTLM automatic submission in a Windows environment:
<ol>
<li> Browsers automatically send NTLM when needed to cached web application with Intranet URL and some (e.g. default Internet Explorer) will send it even to non-cached intranet sites.</li>
<li> Use template based word this will trigger SMB communication with  NTLM.</li>
<li> Use XXE on servers</li>
<li> Use SQL Injection techniques</li>
</ol>
</p>

<p>
<h2>Quick PoC Instructions:</h2>
<ol>
<li> Locate a web application which requires NTLM authentication</li>
<li> Launch NHASTIE with the following command on the attacker's machine:<br>
java -jar -t {Target IP or Hostname} -p {Target Port} -l {listen port} {-ssl optional}</li>
<li> Lure/Phish/Spoof/Trick/MITM/XSS/CSRF the victims browser to connect to
NHASTIE server using regular HTTP* (NHASTIE does SSL Stripping)</li>
<li> Open a browser, connect to NHASTIE, and surf in the web application with the victim's session.</li>
</ol><br>
* It is possible to execute to combine this attack with cross protocols
</p>

<p>
<h2>Developers</h2>
NHASTIE is developed and maintained by <a href="https://twitter.com/oren1ofer">Oren Ofer (@oren1ofer)</a>.
</p>

<p>
<h2>Latest Version Changes</h2>
Version 1.2
<ol>
<li>Built in support for SSL: use flag -ssl when needed</li>
<li>Some bug fixes</li>
</ol>
</p>

<p>
<h2>Copyright</h2>
</p>
<p>NHASTIE - NTLM HTTP Authentication Session Tier Exploit.</p>

<p>Copyright (C) 2014, Hacktics ASC, Ernst & Young.</p>

<p>Licensed under the Apache License, Version 2.0 (the "License");</p>
<p>you may not use this file except in compliance with the License.</p>
<p>You may obtain a copy of the License at</p>

<p>http://www.apache.org/licenses/LICENSE-2.0</p>

<p>Unless required by applicable law or agreed to in writing, software</p>
<p>distributed under the License is distributed on an "AS IS" BASIS,</p>
<p>WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.</p>
<p>See the License for the specific language governing permissions and</p>
<p>limitations under the License.</p>

</article>