---
title: "Introduction to OT Protocols"
date: 2022-09-24T08:43:01+02:00
featured: true
categories: [ot]
tags: [security, protocols, ot]
draft: false
---

# Introduction to some OT protocols

## Modbus
### Modbus RTU
Modbus RTU is a serial communication protocol that allows data exchange between PLCs and PCs.


### Modbus TCP

To find devices using Modbus, we can use the following nmap script:

`nmap --script modbus-discover.nse -p 502 <host>`

### Modbus TCP
Modbus TCP is a variant of Modbus RTU over TCP/IP. 

Common Port: 502/TCP

To find devices using Modbus TCP, we can use the following Nmap script:

```bash
nmap --script modbus-discover.nse -p 502 <host>
```

## OPC UA

OPC Unified Architecture (UA) is another communication protocol for industrial automation. It is more secure and flexible than older OPC versions.

Common Port: 4840/TCP

Tools:
- Prosys OPC UA Simulation Server (for testing)
- UaExpert (client)
- Nmap script (OPC UA):

```bash
nmap --script opc-ua-info -p 4840 <host>
```

## Zigbee

Zigbee is a wireless communication protocol used in IoT and industrial control systems. It operates over IEEE 802.15.4.

Common Frequency: 2.4 GHz (no standard TCP/UDP port)

Tools:
- KillerBee toolkit
- ZBOSS Sniffer
- HackRF / RZUSBstick 

Common Commands:
```bash
zbid
zbstumbler
zbfind
```

## DNP3

Distributed Network Protocol 3 is used in utilities like electric and water companies. It is designed for SCADA systems.

Common Port: 20000/TCP

Tools:
- Wireshark (with DNP3 dissector)
- Scapy for crafting DNP3 packets
- Nmap script:

```bash
nmap -sV -p 20000 <host>
```

## BACnet

BACnet is a communication protocol for building automation and control networks.

Common Port: 47808/UDP (also known as port 0xBAC0)

Tools:
- BACnet Stack (for custom applications)

- Nmap script:

```bash
nmap --script bacnet-info -p 47808 <host>
```

## MQTT

MQTT is a lightweight messaging protocol used for small sensors and mobile devices.

Common Port: 1883/TCP (unencrypted), 8883/TCP (encrypted)

Tools:
- MQTT Explorer
- Mosquitto client

- Nmap script:

```bash
nmap -sV -p 1883,8883 <host>
```


## Profinet

Profinet is an industry technical standard for data communication over Industrial Ethernet, designed for collecting data from and controlling equipment in industrial systems.

Common Port: 34964/UDP, 34962/UDP

Tools:
- Wireshark (with Profinet dissector)
- PNIO Test Tools

## EtherNet/IP

EtherNet/IP is a widely used industrial network protocol that implements the Common Industrial Protocol (CIP) over standard Ethernet.

Common Port: 44818/TCP and UDP

Tools:
- cpppo (Python library)
- Nmap script:

```bash
nmap -sV -p 44818 <host>
```

## IEC 60870-5-104

IEC 60870-5-104 is a protocol used for telecontrol in electrical engineering and power system automation applications.

Common Port: 2404/TCP

- Nmap script:

```bash
nmap -sV -p 2404 <host>
```

## HART-IP

HART-IP enables communication between HART devices and host applications over IP networks.

Common Port: 5094/TCP

Tools:
- FieldComm Group tools

## EnIP (ControlNet/DeviceNet over Ethernet)

EnIP (Ethernet Industrial Protocol) supports both ControlNet and DeviceNet over Ethernet.

Common Port: 2222/UDP (I/O Messaging)

Tools:
- cpppo
