# Natas Level 9 → Level 10
<pre><h3><b>Level 9
Username : natas9
Password : W0mMhUcRRnG8dcghE4qvk3JA9lGt8nDl
URL      : http://natas9.natas.labs.overthewire.org</b></h3></pre>
### Solution

To solve this level, we first log into the natas9 application using the credentials provided above.

After logging in, we can see that the application looks like a search application which searches for input characters in a dictionary. Upon looking at the source code, we can see that the dictionary is available here **http://natas9.natas.labs.overthewire.org/dictionary.txt**.

The application code utilizes `passthru()` function to grep for the searched term using a GET parameter '**needle**'. The passthru() function is similar to the exec() function in that it executes a command. This function should be used in place of exec() or system() when the output from the Unix command is binary data which needs to be passed directly back to the browser.

As we can see, the application does not validate the data entered in the GET parameter and simply passes it to the passthru function call. Therefore, the passthru function seems vulnerable. Lets validate this by passing ` ;echo hello; `. The passthru function performs the query ` passthru(“grep -i;echo hello;dictionary.txt”);` and prints hello on the screen.

If we pass the file location of the password for natas10, the application should respond back with the password. We now pass ` ; cat /etc/natas_webpass/natas10;  ` as the search term and Voila!, the application responds with the password for natas10.

<pre><h3><b>Level 10
Username : natas10
Password : nOpp1igQAkUzaI1GUUjzn1bFVj7xCNzu
URL      : http://natas10.natas.labs.overthewire.org</b></h3></pre>
