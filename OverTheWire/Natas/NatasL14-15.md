---
layout: post
title: Natas Level 14 → Level 15
excerpt: "Solving Natas Level 14"
tags: [Overthewire, Natas]
comments: true
category: blog
---

# Natas Level 14 → Level 15
<pre><h3><b>Level 14
Username : natas14
Password : Lg96M10TdfaPyVBkJdjymbllQ5L6qdl1
URL      : http://natas14.natas.labs.overthewire.org</b></h3></pre>
### Solution

To solve this level, we first log into the natas14 application using the credentials provided above.

The application presents a form for a **username** and **password** field. On checking the source code of the application, we can see that the application checks whether the credentials provided by a user results in atleast 1 row or not. Therefore, if the combination username and password match an existing entry in the table, the application will return the password for the next level.

```
<?
if(array_key_exists("username", $_REQUEST)) {
 $link = mysql_connect('localhost', 'natas14', '');
 mysql_select_db('natas14', $link);
 
 $query = "SELECT * from users where username=\"".$_REQUEST["username"]."\" and password=\"".$_REQUEST["password"]."\"";
 if(array_key_exists("debug", $_GET)) {
 echo "Executing query: $query";
 }

if(mysql_num_rows(mysql_query($query, $link)) > 0) {
 echo "Successful login! The password for natas15 is ";
 } else {
 echo "Access denied!";
 }
 mysql_close($link);
} else {
?>
```
To make things easier to understand, the application also provides us with a GET variable, debug. We can see the exact query run by the application if this variable exists in the request.
With this information, we can start brute-forcing our way into the application. We can try the most common credentials like (**admin/admin, admin/password, etc**). Let’s set the debug variable and see how the application runs the query.

We can see that the query that is ran for **admin/admin** is:

```
SELECT * from users where username="admin" and password="admin"
```

Just like some of the previous levels, its clear that the application does not validate/verify the user input and simply uses it to run a query. Let’s see how the application responds to an unexpected user input like **admin”/admin**.

We can see that the application returns an **Access Denied.**, however, this time the application also throws a warning **mysql_num_rows() expects parameter 1 to be resource, boolean given in /var/www/natas/natas14/index.php on line 24**. Lets look at the query that was ran by the application this time :
```
SELECT * from users where username="admin"" and password="admin"
```

We can see that an unexpected character results in an invalid SQL statement which breaks the application. Lets exploit this vulnerability which is commonly known as SQL Injection. This time around, we will not break the application but rather try to return more than one row which will result in application thinking that we know the correct username and password and thus returning the password for the next level.

First let’s understand what happens when a query like the following is ran on a database:

```
SELECT * from users where username="value1" OR "1"="1";
```

As we know that in a case like this if one of the OR conditions returns a true, the whole statement returns true. Therefore, by using the same logic, we can make the application server return **true** in the **where** clause which will result in the application returning all the rows in the table.

Let’s user the username and password as **admin” OR “1”=”1**. Note that the last “ sign is provided by the application when it creates the query. The query run by the server in this case will be:

```
SELECT * from users where username="admin" OR "1"="1" and password="admin" OR "1"="1"
```

We now have the password for the next level.

<pre><h3><b>Level 15
Username : natas15
Password : AwWj0w5cvxrZiONgZ9J5stNVkmxdk39J
URL      : http://natas15.natas.labs.overthewire.org</b></h3></pre>
