# Natas Level 4 → Level 5
<pre><h3><b>Level 4
Username : natas4
Password : Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ
URL      : http://natas4.natas.labs.overthewire.org</b></h3></pre>
### Solution

To solve this level, we first log into the natas4 application using the credentials provided above.

![natas4-1](https://securitytimes.files.wordpress.com/2017/06/c.png?w=663)

Upon logging in, we can see the message displayed by the application ‘**Access disallowed. You are visiting from “” while authorized users should come only from http://natas5.natas.labs.overthewire.org/&#8221;**

This message from the application gives us a hint that probably the application is only allowing access to requests referred by **http://natas5.natas.labs.overthewire.org/**

Each HTTP message contains headers that are used to exchange information about the content of the HTTP message. One of the headers is Referer. (The misspelling of referrer originated in the original proposal by computer scientist Phillip Hallam-Baker to incorporate the field into the HTTP specification. Referer has since become a widely used spelling in the industry when discussing HTTP referrers)

For this particular case, I am going to use Burp Proxy to send this request and add a Referer header with the value **http://natas5.natas.labs.overthewire.org/**.

![natas4-2](https://securitytimes.files.wordpress.com/2017/06/7-10-2017-3-24-08-pm.png?w=663)

As we can see in the screenshot above, the password for **natas5** is displayed.

<pre><h3><b>Level 5
Username : natas5
Password : iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq
URL      : http://natas5.natas.labs.overthewire.org</b></h3></pre>
