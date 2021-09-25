---
title: "Nmap: basic guide for pentesting"
date: 2021-09-21T20:40:40+02:00
categories: [security]
tags: [nmap]
draft: false
---

Nmap is a well-known tool for pentesters and hackers. It basically allows us to scan the ports of a network, but it is much more powerful than that, as we will see in this post. We will start by reviewing some basic commands of nmap.

## Scanning ports


We can use the following command to perform an scan of the specified port of the address given. This will show us which ports are open, closed, or protected by some firewall. Moreover, it will show us which services are running. If we don't specify a port, it will scan the 1000 most common ports.

	nmap IP -p PORT

We can obtain more information about the versions of the services and applications running in each port using the option `-sV`.

	nmap -sV IP -p PORT
	
The command `-A` allows us to detect the versions but also the operating system

	nmap -A IP -p PORT

We can also use the `-O` option to detect the operating system

	nmap -O IP -p PORT
	
## Timming

Nmap has a parameter -T, which specifies the different delays. There is more information [available here]( https://nmap.org/book/performance-timing-templates.html), but we will cover the basics:

-T0 (paranoid): Used to bypass IDS.    
-T1 (sneaky): Also used to bypass IDS, but not so slow as T0.   
-T2 (polite): Slow scan.  
-T3 (normal): Normal mode.  
-T4 (aggressive) : Faster than normal. Only recommended on a fast network.  
-T5 (insane) : Fastest scan. Assumes you are in a really fast and reliable network.  

## IDS/Firewall evasion

Some other options to bypass IDS and Firewalls are the options `-f` and `-mtu`. The first one will send small fragmented IP packages, which will make it hard for the systems to detect the scan. This option will divide the packages in 8 bytes fragments. The option `-mtu` allows you to specify your own size.

**Note**: you can only use one of those options.

## Vulnerability scanning


Nmap also has a variety of scripts that we can use for vulnerability scanning and explotation. If we want to look for scripts for a particular server, we can do it by typing:

	nmap --script-help "http-*"
	

And it will print us all the scripts matching the service/application and how to use them.

It also accepts the * wildcard and the boolean operators `and`, `or` and `not`. We can execute several scripts separated by a comma.

	nmap ---script  http-enum IP

If the script has arguments, we can specify them with the option `--script-args <n1>=<v1>`.

# Output

The option `-oN` allows us to redirect the output to a file. The option `-oX` redirects the output to a specified file as an XML. 

	nmap IP -oN output.txt
	


In the next post about nmap I will be covering some advanced nmap options.
