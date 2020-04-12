What is reflected cross-site scripting?
Reflected XXS arises when an application recieves data in an HTTP request and includes that data within the immediate repsonse   
in an unsafe way.  

Suppose a website has a search fucntion which recieved the user suppiled search term in a url parameter 
https://insecure-website.com/search?term=gift

The application echoes the supplied search term in the response to this URL 
<p>You searched for: gift</p>

Assuming the application doesn't perform any other processing of the data, attackers can construct an attack like this. 
https://insecure-website.com/status?message=<script>/*+Bad+stuff+here...+*/</script>

Lab: Reflected XSS into HTML context with nothing encoded
web-security-academy.net/?search=<script>alert(1)</script>



