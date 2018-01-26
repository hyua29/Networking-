./shutdown.sh

find the process that is using the port
==========================================
- lsof -i :8080
- kill _pid

configure the server
=====================
- setting is in /Coding/apache-tomcat/conf/server.xml


what if the website cannot be accessed by other devices
==========================================================
down vote
accepted
This question is probably better asked on ServerFault,

I guess your Tomcat binds to the Local Interface and thus is not accessible from the outside world.

If you would like to make Tomcat serve requests from any other host (same wifi network AND the internet), change your Connector in the server.xml config file (See official Docs for details)

    <Connector port="8080" 
       protocol="HTTP/1.1" 
       address="0.0.0.0"
       connectionTimeout="20000"
       redirectPort="8443" />
The important part is address="0.0.0.0" which binds your tomcat to all network interfaces.

It this is already in place there might also be a firewall or other windows networking settings blocking incoming requests.

If you can reach Tomcat, but get an error message such as 404 not found, make sure you are using the correct URL:

http://<TomcatHostOrIP>:8080/Context/
Where Context is usually the name of your war-file.

Get and POST
=============
- GET
	- can be bookmarked on url
	- easy to debug 
	- can be set and seen on the url
	- non-sensetive
- POST
	- can send large data
	- embedded into the html file
	- can also send binary data
	- sensetive
	- simple encryption 

MVC
====
- html send to servlet
- servlet process the request 
- call utilty class to get data
- data retrieved from the database is stored in the ArrayList as an object
- servlet forward ArrayList to jsp
- jsp is responsible for rendering the page

Resource Pool
==============
- [tomcat reference](http://tomcat.apache.org/tomcat-8.5-doc/jndi-datasource-examples-howto.html)
- reuse the connection and hence can improve performance
- copy files under web in jsp_test

close the connection 
=======================
- need to close the database connection once the process is finished 
- otherwise there might be a memory leak or the app runs out of memory/curser in the next few days/weeks 
- when using resource pool, 'connection.close() does not really close the connection. It acctually puts the connection back to the pool and marks it as available so that it can be reused again 

	
 

