PyPunchP2P
==========

Python p2p chat client/server with built-in NAT traversal (UDP hole punching).  
I've write [an article][4] about the detailed implementation (in Chinese).

Based on  
[koenbollen's gist][1]  
[pystun][2]  
[Peer-to-Peer Communication Across Network Address Translators][3]

Python edition: py2.6+ but no Python 3 support  
Platform: Linux/Windows

usage
-----
Suppose you run server.py on a VPS with ip 1.2.3.4, listening on port 5678  
```bash
$ server.py 5678
```  

client A and client B:  
```bash
$ client.py 1.2.3.4 5678 100  
```  
The number `100` is used to match clients, i.e. clients with the same number will be linked by server.

Test
----
You could do simulation testing by specifying a fourth parameter of `client.py`, it will assume that your client is behind a specific type of NAT device.

Here are the corresponding NAT type and number:  

	FullCone         0  
	RestrictNAT      1  
	RestrictPortNAT  2  
	SymmetricNAT     3   

So you might run
```bash
$ client.py 1.2.3.4 5678 100 1
```   
pretending your client is behind RestrictNAT.

[1]:https://gist.github.com/koenbollen/464613
[2]:https://pypi.python.org/pypi/pystun
[3]:http://www.bford.info/pub/net/p2pnat/index.html
[4]:http://www.laike9m.com/blog/pythonshi-xian-stunturnp2pliao-tian,29/














