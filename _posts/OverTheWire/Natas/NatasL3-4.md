# Natas Level 3 → Level 4
<pre><h3><b>Level 3
Username : natas3
Password : sJIJNW6ucpu6HPZ1ZAchaDtwd7oGrD14
URL      : http://natas3.natas.labs.overthewire.org</b></h3></pre>
### Solution

To solve this level, we first log into the natas3 application using the credentials provided above.

![natas3-1](https://securitytimes.files.wordpress.com/2017/06/7-10-2017-3-06-48-pm.png?w=663)

After logging in, we can see the message ‘**There is nothing on this page**‘. Upon examining the page HTML we can see a comment ‘**No more information leaks!! Not even Google will find it this time…**‘

The robots exclusion standard, also known as the robots exclusion protocol or simply robots.txt, is a standard used by websites to communicate with web crawlers (like Google) and other web robots. The standard specifies how to inform the web robot about which areas of the website should not be processed or scanned. Robots are often used by search engines to categorize web sites. Not all robots cooperate with the standard; email harvesters, spambots, malware, and robots that scan for security vulnerabilities may even start with the portions of the website where they have been told to stay out. The standard is different from, but can be used in conjunction with, Sitemaps, a robot inclusion standard for websites.

Upon accessing **http://natas3.natas.labs.overthewire.org/robots.txt** we can see that the administrator does not want a web crawler like Google to access ‘**/s3cr3t/**‘. In the context of robots.txt files, security through obscurity is not recommended as a security technique. We now access the folder and find a users.txt file. Upon opening that file, we find the password for the next round.

![natas3-2](https://securitytimes.files.wordpress.com/2017/06/7-10-2017-3-07-46-pm.png)
![natas3-3](https://securitytimes.files.wordpress.com/2017/06/7-10-2017-3-08-14-pm.png)
![natas3-4](https://securitytimes.files.wordpress.com/2017/06/7-10-2017-3-08-39-pm.png)

<pre><h3><b>Level 4
Username : natas4
Password : Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ
URL      : http://natas4.natas.labs.overthewire.org</b></h3></pre>
