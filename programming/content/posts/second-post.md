---
title: "Nmap: basic guide for pentesting"
date: 2021-09-21T20:40:40+02:00
draft: false
---

Nmap is a well-known tool for pentesters and hackers. It basically allows us to scan the ports of a network, but it is much more powerful than that, as we will see in this post.

## Scanning ports with Nmap

We can use `nmap IP  -p PORT` to perform an scan of the 1000 most important ports of the specified address. This will show us which ports are open, closed, or protected by some firewall. Moreover, it will show us which services are running.

## Bypassing detection

Nmap has different ways of bypassing detection. In this post, we will present two ways:

We can use the T parameter, specifying the delay 

Or we can use -Pn

## Vulnerability scanning

