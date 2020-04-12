## Web Academy Cross-Site Scripting (XSS) 

#### What is Cross-Site Scripting(XSS) 
XSS is a type of computer security vulnerability found in web applications. XSS attacks enable attackers to inject **client-side scripts** into web pages viewed by other users. This type of vulnerability allows an attacker to circumvent the **same origin policy**, which is designed to segregate different websites from each other. 

#### How does XSS Work ? 
XXS works by manipulating a vulnerable web site so that it returns malicious JavaScript to users. When the malicious code executes inside a victim's browser, the attacker can compromise their intereaction w/ the webapp. 

#### What are the types of XSS attacks? 
1) Reflected XSS, where the malicious scripts comes from the current HTTP request
2) Stored XSS, where the malicious script comes the website's database
3) DOM-based XSS, where the vulnerability exists in client-side code rather than server-side code.

#### Impact of XSS vulnerabilities 
The impact of the XSS attack is based on the nature of the application, and it's functionality, data, anda the type of compromised user(ex, admin user)  

#### How to protect again XSS attacks
**Filter input ** - At the point where user input is recieved , filter as strictly as possible based on what is expected 
** Encode data on output** - At the point where user-controllable data is output in HTTP reponses, encode the output to prevent it from being interpreted as active content 
**Content Security Policy ** - As a last line of defense, you can use Content Security Policy (CSP) to reduce the severity of any XSS vulnerabilities that still occur.
 
