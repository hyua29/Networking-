Basic networking 
=====

OSI model 
- Open Systems Interconnection model
- Application layer</br>
  Presentation layer</br>
  Session layer</br>
  Transport layer</br>
  Network layer</br>
  Data link layer</br>
  Physical layer</br>

[TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)
- Transmission Control Protocol
- The TCP segment is then encapsulated into an Internet Protocol (IP) datagram
- three-way handshake to initialise and four-way handshake to terminate
- Error detection
	- Sequence numbers allow receivers to discard duplicate packets and properly sequence reordered packets.
	- Acknowledgments allow senders to determine when to retransmit lost packets.
- Flow control 
	- In each TCP segment, the receiver specifies in the receive window field the amount of additionally received data (in bytes) that it is willing to buffer for the connection.
	  The sending host can send only up to that amount of data before it must wait for an acknowledgment 
	  and window update from the receiving host.
	- The persist timer is used to protect TCP from a deadlock situation
	- When the signal is weak, the receiver notifies the server to lower the transmission rate



TCP is a mechanism that allows us to transfer data safely; </br>
and HTTP, which utilizes TCP to transfer its data, is a specific protocol used by Web servers and clients.</br>
-----------------------------------------------------------------------------------------------------------------------------
[Sunbet Mask](https://en.wikipedia.org/wiki/Subnetwork)
- This logical addressing structure permits the selective routing of IP packets across multiple networks via special gateway computers, called routers, to a destination host if the network prefixes of origination and destination hosts differ, or sent directly to a target host on the local network if they are the same. 
- Determining the network prefix
An IPv4 network mask consists of 32 bits, a sequence of ones (1) followed by a block of zeros (0). The trailing block of zeros designates that part as being the host identifier.
The following example shows the separation of the network prefix and the host identifier from an address (192.168.5.130) and its associated /24 network mask (255.255.255.0). The operation is visualized in a table using binary address formats.

| Binary form  |	Dot-decimal                | notation      |
|--------------|:---------------------------------:|--------------:|
|IP address    |11000000.10101000.00000101.10000010| 192.168.5.130 |
|Subnet mask   |11111111.11111111.11111111.00000000| 255.255.255.0 |
|Network prefix|11000000.10101000.00000101.00000000|192.168.5.0    |
|Host part     |00000000.00000000.00000000.10000010|	0.0.0.130  | 
The result of the bitwise AND operation of IP address and the subnet mask is the network prefix 192.168.5.0. The host part, which is 130, is derived by the bitwise AND operation of the address and the one's complement of the subnet mask.
- Subnetting
Subnetting is the process of designating some high-order bits from the host part and grouping them with the network mask to form the subnet mask. This divides a network into smaller subnets. The following diagram modifies the example by moving 2 bits from the host part to the subnet mask to form four smaller subnets one quarter the previous size:
|Binary form   |	Dot-decimal                |  notation      |
|--------------|:---------------------------------:|---------------:|
|IP address     |11000000.10101000.00000101.10000010|192.168.5.130  |
|Subnet mask    |11111111.11111111.11111111.11000000|255.255.255.192|
|Network prefix |11000000.10101000.00000101.10000000|192.168.5.128  |
|Host part      |00000000.00000000.00000000.00000010|0.0.0.2        |
- More subnet
A /24 network may be divided into the following subnets by increasing the subnet mask successively by one bit. This affects the total number of hosts that can be addressed in the /24 network (last column).
|Prefix size| Subnet mask| Available subnets| Usable hosts per subnet|	Total usable hosts|
|-----------|:----------:|:----------------:|:----------------------:|
-----------------:|
|/24|	255.255.255.0	|1	|254	|254|
|/25|	255.255.255.128	|2	|126	|252|
|/26|	255.255.255.192	|4	|62	|248|
|/27|	255.255.255.224	|8	|30	|240|
|/28|	255.255.255.240	|16	|14	|224|
|/29|	255.255.255.248	|32	|6	|192|
|/30|	255.255.255.252	|64	|2	|128|
|/31|	255.255.255.254	|128	|2 *	|256|

Broadcast address
- A broadcast address is a logical address at which all devices connected to a multiple-access communications network are enabled to receive datagrams. A message sent to a broadcast address is typically received by all network-attached hosts, rather than by a specific host.
- The broadcast address for an IPv4 host can be obtained by performing a bitwise OR operation between the bit complement of the subnet mask and the host's IP address. In other words, take the host's IP address, and set to '1' any bit positions which hold a '0' in the subnet mask.
- Example: For broadcasting a packet to an entire IPv4 subnet using the private IP address space 172.16.0.0/12, which has the subnet mask 255.240.0.0, the broadcast address is 172.16.0.0 | 0.15.255.255 = 172.31.255.255.


IP
- Internet Protocol 
- size of the ip datagram is specified at ip header

UDP
- User Datagram Protocol 
- not reliable data stream

RTP
Real-time Transport Protocol 

UA
- user agent
- e.g. browser, mobile apps and other software that accesses, consumes, or displays web content

[URL](https://en.wikipedia.org/wiki/URL)
- Uniform Resource Locators 
-A typical URL could have the form http://www.example.com/index.html, 
which indicates a protocol (http), a hostname (www.example.com), and a file name (index.html).
- syntax: scheme:[//[user[:password]@]host[:port]][/path][?query][#fragment]

[HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
- HTTP/1.1 can reuse a connection multiple times 
to download images, scripts, stylesheets, etc after the page has been delivered
- less establishments of TCP connections
- Request methods '
	- GET 
		- requests a representation of the specified resource.
		  Requests using GET should only retrieve data and should have no other effect
	- HEADER 
		- The HEAD method asks for a response identical to that of a GET request, 
		  but without the response body. This is useful for retrieving meta-information written in response headers, 
		  without having to transport the entire content.
	- POST 
		- POST's place in the range of HTTP methods is to send a representation of a new data entity to the server 
		  so that it will be stored as a new subordinate of the resource identified by the URI.[1] 
		  For example, for the URI http://example.com/customers, POST requests might be expected to represent new customers,
		  each including their name, address, contact details and so on
		
		  ***A block of data that is the result of submitting a web form to a data-handling process;*** 
		  or an item to add to a database.[14]
		  including ***login*** message

- the first line of the HTTP response is called the status line and includes a numeric status code (such as "404") 
  and a textual reason phrase (such as "Not Found").
  Informational 1XX, Successful 2XX, Redirection 3XX, Client Error 4XX and Server Error 5XX.
- Persistent connections
  - no new SYNs</br>

[TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security) and [see public key](https://en.wikipedia.org/wiki/Public_key_certificate)
- SSL is the old name: Secure Sockets Layer 
- Transport Layer Security § Security
- If parts of the site are accessed with HTTP instead of HTTPS, 
  the user and the session will get exposed. 
- ***A server is required to present a certificate as part of the initial connection setup.***
- A client connecting to that server will perform the certification path validation algorithm
    - The subject of the certificate matches the hostname to which the client is trying to connect.
    - The certificate is signed by ***a trusted certificate authority***.

[CA](https://en.wikipedia.org/wiki/Certificate_authority)
- certificate authority
- [watch vedio](https://www.youtube.com/watch?v=DWQpxiXwccQ)
- CA certification happens when the packets are sent and are installed at both ends
- Server certificates typically are issued to hostnames, which could be a machine name (such as ‘XYZ-SERVER-01’) or 
  domain name (such as ‘www.symantec.com’)
	- a web site operator obtains a certificate by applying to a certificate provider with a certificate signing request
- A certificate authority (CA) is an organization that ***stores public keys and their owners***(server's domain name and their public keys?),
  and every party in a communication trusts this organization (and knows its public key).
- allow the client to trust the server and vise versa
- when the client wants to send message to B:
  client(A) encrypts its message with private key of A. This message can only be decrypted by public key of A which is decrypted by the private key
  of a certificate athourity and need a public key of CA to decrypt; so a public key certificate of A needs to sent at the same time to allow
  receiver(B) to know that is the public key of A. The whole thing(encrypted message and public key certificate of A) are both encrypted by the public key of B, 
  and only B with the private key of itself can see that the message is 
- since the message a client send to the server is encrypted by the public key of server; only the server can decrypt it
    - by doing this, the attacker ***cannot read the message*** by intercepting the packets
    - ***This mechanism is only safe if the user can be sure that it is the bank that they see in their web browser***
- When the user's web browser receives the public key from www.bank.example it also receives a digital signature of the key 
    - If the user types in www.bank.example, but their communication is hi-jacked and a fake web-site 
      (that pretends to be the bank web-site) sends the page information back to the user's browser, 
      the fake web-page can send a fake public key to the user (for which the fake site owns a matching private key).
      The user will fill the form with their personal data and will submit the page. The fake web-page will then get access
      to the user's data.
        - ***The browser already possesses the public key of the CA and consequently can verify the signature, 
	  trust the certificate and the public key in it.since www.bank.example uses a public key that 
	  the certification authority certifies(this packet has to pass CA because only CA can sign it with CA's private key),***
	  a fake www.bank.example can only use the same public key. Since the fake www.bank.example does not know the corresponding private key, 
	  it cannot create the signature needed to verify its authenticity.
	- the client 
- [CA认证原理上](http://yale.iteye.com/blog/1675344)
- [CA认证原理下](http://yale.iteye.com/blog/1675355)

man-in-the-middle attack
- A certificate is essential in order to circumvent a malicious party which happens to be on the route to a target server 
  which acts as if it were the target. 
  
[Malware](https://en.wikipedia.org/wiki/Malware)
- ?
- ?

[Packet Injection](https://en.wikipedia.org/wiki/Packet_injection)
- ?
- ?

[VPN](https://en.wikipedia.org/wiki/Virtual_private_network)
- virtual private network 





-





