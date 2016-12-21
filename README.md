PyPunchP2P
==========

### THIS PROJECT IS FOR STUDYING AND VERIFICATION, DON'T USE IT IN PRODUCTION.

Python p2p chat client/server with built-in NAT traversal (UDP hole punching).  
I've written [an article][4] about the detailed implementation (in Chinese).

Based on  
[koenbollen's gist][1]  
[pystun][2]  
[Peer-to-Peer Communication Across Network Address Translators][3]

Python edition: py2.6+ but no Python 3 support  
Platform: Linux/Windows

Usage
-----
Suppose you run server.py on a VPS with ip 1.2.3.4, listening on port 5678  
```bash
$ server.py 5678
```  

On client A and client B (run this on both clients):  
```bash
$ client.py 1.2.3.4 5678 100  
```  
The number `100` is used to match clients, you can choose any number you like but only clients with the **same** number will be linked by server. If two clients get linked, two people can chat by typing in terminal, and once you hit `<ENTER>` your partner will see your message in his terminal.   
Encoding is a known issue since I didn't pay much effort on making this tool perfect, but as long as you type English it will be fine.

Test Mode
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
You can test the relay server functionality by making `3` as the forth parameter, since if one client is behind symmetric NAT, there will be no direct connection but server forwaring.

License
-------
MIT

[1]:https://gist.github.com/koenbollen/464613
[2]:https://pypi.python.org/pypi/pystun
[3]:http://www.bford.info/pub/net/p2pnat/index.html
[4]:http://www.laike9m.com/blog/pythonshi-xian-stunturnp2pliao-tian,29/














