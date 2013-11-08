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
<li> nhastie requires Java <u>1.7.x</u></li>
</ul>
</p>

<p><h2>How Does it Work?</h2>
NTLM HTTP authentication is based on a TCP connection, i.e. the connection is the session (I call it "ConSessions"). In order to exploit this fact here is what NHASTIE does:
<ol>
<li> The tool creates a single TCP socket which will be used to transfer all communication to and from the target web application, and stands by (listening) for a victim.</li>
<li> A victim issues an HTTP request to the tool and the tool forward the HTTP request to the designated web application.</li>
<li> The Web application replies with a demand to authenticate using NTLM, the tool forwards the response to the victim.</li>
<li> The victim automatically responds with a valid NTLM authentication, which is forwarded by the tool the web application by the same TCP socket.</li>
<li> The web application treat all future incoming HTTP requests from this TCP socket as authenticated by the victim.</li>
<li> The attacker connects to the tool using a browser, and surfs the vulnerable web application using the victim's identity!</li>
</ol>
</p>

<p><h2>Can Attackers Make Victims Connect to this Tool?</h2>
Yes, and in numerous ways, for example:
<ol>
<li> Asking - Be nice :)</li>
<li> Phishing - Luring users to use a link, open of template based word, etc.</li>
<li> Using web application attacks - XSS, CSRF, etc.</li>
<li> Forcing with MITM</li>
</ol>
Several instances that will trigger NTLM automatic submission in a Windows environment:
<ol>
<li> Browsers automatically sends NTLM when needed to cached web application with Intranet URL and some (e.g. default Internet Explorer) will send it even to none cached intranet sites.</li>
<li> Use template based word this will trigger SMB communication with  NTLM.</li>
<li> Use XXE on servers</li>
<li> Use SQL Injection techniques</li>
</ol>
</p>

<p>
<h2>Quick PoC Instructions:</h2>
<ol>
<li> Launch NHASTIE with the following command on the attacker's machine:<br>
java -jar nhastie.jar {}</li>
<li> Run Internet Explorer from the victim's machine and surf to the attacker's computer http://attacker</li>
<li> Run a browser from any computer, connect to the attacker's machine, surf using the victim's authenticated channel.</li>
</ol>
</p>

<p>
<h2>Developers</h2>
NHASTIE is developed and maintained by <a href="https://twitter.com/oren1ofer">Oren Ofer (@oren1ofer)</a>.
</p>

<p>
<h2>Copyright</h2>
</p>
<p>NHASTIE - NTLM HTTP Authentication Session Tier Exploit.</p>

<p>Copyright (C) 2013, Hacktics ASC, Ernst & Young.</p>

<p>This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.</p>

<p>This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.</p>

<p>You should have received a copy of the GNU General Public License along with this program.  If not, see <a href="http://www.gnu.org/licenses/">http://www.gnu.org/licenses</a>.</p>

</article>