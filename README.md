# DnsTunnelingTool
A project created for the course Advance Cyber Topics

In this project we have built a tool that can help indentify data exfiltraition over dns protocol vulnerability.

This tool can illustrate a malware that can exfiltrait data from a pc to a maliciouse DNS server over DNS queries.

It can use 3 different modes and also it is possible to controle the rate of the queries.

you can use this tool in all of it's differents mode and different rates in order the check if your existing protection tools can identify the attack,
if not you will know exactly what were the settings of the attack and it help you configurating your protection tools. 

HOW TO USE THE TOOL:

	Go to "configuration file.txt".
	This file contains the following fields:
	-------------------------------------------------------------------------------------------------------
	-------------------------------------------------------------------------------------------------------
		1)seconds_between_query -
			this is where you can choose the anount of seconds between DNS queries. 
			This field can help check if the protection tools can identify attacks that are "low and slow".
	------------------------------------------------------------------------------------------------------
	------------------------------------------------------------------------------------------------------
		
		2)method-
			This is where you can decide what method to use
			there are 3 method.
			______________________________________________________________________________________________
			a) ip_based - this method will send a dns query directly to the maliciouse DNS server.
						  Also in this method the DNS query will be spoofed so that the souorce IP will be the IP of the local DNS server in order to overcome firewall rules. 
						  In addition the DNS query will be a regular domain so that it will look like a legitimate query.
			for this method we used a dictionary that maps letters to domains so that every letter in the credit card file will be sent as a different domain.
			for example the word "Visa" will tranlste to 4 DNS queries look with this domains:aliexpress.com , aboutads.info , akamaihd.net , webhost.com.
			we also mapped chrarchters like " ,\n." etc. for making it easy to parse.
			
			*** the ip for the maliciouse DNS server is also taken from the configuration file*** 
			______________________________________________________________________________________________
			
			b) domain_based - this method will send a regular DNS query to it's local DNS server but it will map every letter to a word and will concat it with the maliciouse domin, we do this so that the query looks like a legitimate query.
			for this method we used dictionary that maps letters to regular words so that every letter in the "credit card.exe" file will be sent as a different word concated with the maliciouse domain prefix.
			for example: the word Visa will be send as 4 diiferent queries look like this: Woman.maliciouse.com , Sixty.maliciouse.com, Piano.maliciouse.com, Seven.maliciouse.com.
			to make sure that every query will get to oure maliciouse DNS server and not be answered from a DNS server that ceched our queries, we are sending a uniqe query each time. 
			
			______________________________________________________________________________________________
			
			c) domain_based64 - same as domain_based but this method will take each word in the "credit card.txt" file and encode it with base64 ebcoder.
								for example: the word Visa will send as  VmlzYQ==.malicious.com.
								
	-------------------------------------------------------------------------------------------------------
	-------------------------------------------------------------------------------------------------------
		
		3) domain_name - 
				Here you insert your domain of your authoritative dns server that methods "domain_based" , "domain_based64" will use 
				to send the DNS query to.
		
	-------------------------------------------------------------------------------------------------------
	-------------------------------------------------------------------------------------------------------
	
		4) dns_server_ip - 
				Here you insert your IP address of your malicious DNS server that the method "ip_based" will use to send the DNS query.
		
	-------------------------------------------------------------------------------------------------------
	-------------------------------------------------------------------------------------------------------
	
		5) dns_server_port -
				Here you insert the port that your  malicious DNS server is listening on.(also used in the method "ip_based").
		
	-------------------------------------------------------------------------------------------------------
	-------------------------------------------------------------------------------------------------------
	
		6) path_to_data_file -
				Here you insert the Path to the "credit cards.txt" file.
				
	-------------------------------------------------------------------------------------------------------
	-------------------------------------------------------------------------------------------------------
	
		*** THE CONFIGURATION.TXT, DOMAINS.CSV, WORDS.CSV, DNSCLIENT.EXE FILES HAS TO BE IN THE SAME DIRECTORY ***s


