# Natas Level 6 → Level 7
<pre><h3><b>Level 6
Username : natas5
Password : iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq
URL      : http://natas5.natas.labs.overthewire.org</b></h3></pre>
### Solution

To solve this level, we first log into the natas6 application using the credentials provided above.

![natas6-1](https://securitytimes.files.wordpress.com/2017/06/7-10-2017-3-30-02-pm.png?w=663)

We can see that the application provides a text box to enter a secret. Presumably, if the secret matches what the application expects, we should get our password for the next round.

![natas6-2](https://securitytimes.files.wordpress.com/2017/06/7-10-2017-3-30-36-pm.png?w=663)

Looking at the source code, we can see that the application checks the entered value against a secret obtained from the file ‘**includes/secret.inc**‘.  Therefore, if we can find out what that value is, we might be able to obtain the password for the next level.

Upon navigating to **http://natas6.natas.labs.overthewire.org/includes/secret.inc**, we can see that the application shows the password for the next level in a comment. We can now use that secret in the application and Voila!, the application prints the password for the next level.

![natas6-3](https://securitytimes.files.wordpress.com/2017/06/7-10-2017-3-31-22-pm.png)

![natas6-4](https://securitytimes.files.wordpress.com/2017/06/7-10-2017-3-32-02-pm.png?w=663)

<pre><h3><b>Level 7
Username : natas7
Password : 7z3hEENjQtflzgnT29q7wAvMNfZdh0i9
URL      : http://natas7.natas.labs.overthewire.org</b></h3></pre>
