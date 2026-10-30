# h2 "Nuuh" - Nico Defaa

Work environment: Kali Linux 2026.2 Virtual Machine

As with all other weekly exercises, I started by running `sudo apt-get update && sudo apt upgrade -y` on my Virtual Machine to make sure everything is up to date.

<br>

## x) Read and summarize

Task: Read and summarize the two articles: [Wireshark - Getting Started](https://terokarvinen.com/wireshark-getting-started/) and [Network Interface Names on Linux](https://terokarvinen.com/network-interface-linux/) (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

**Wireshark - Getting Started**

- Wireshark is the leading network sniffer and analyzer.
- The user should belong to the *wireshark* group in order to properly capture and view traffic with it.
- Groups update when re-logging in. *newgrp wireshark* can be used to update the group right away on a specific shell.
- Wireshark can be run from command line with *wireshark* (or from the Graphical UI).
- In Wireshark you can select which network interface you want to capture on. "any" is also an option.
- Captured traffic viewing can be filtered in many ways like by protocol, port, IP address or strings. For example *tcp.port == 443*.
- Captures can be saved into **.pcap**-files.

Reference: Karvinen, T. 2025a

<br>

**Network Interface Names on Linux**

- Network interface is like a network card, but it's not always a physical card.
- All computers have the loopback interface for localhost, which has no physical card.
- IPv4 local addresses are 127.0.0.1/8 and IPv6 local addresses are ::1/128.
- You can check your interfaces with *ip a* (ip address) and *ip route*.

Reference: Karvinen, T. 2025b

<br>

## a) Linux

Task: Install Debian or Kali Linux Virtual Machine. (Reference: Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

Already done and documented at the beginning of the [previous week's exercise](https://github.com/nicodefaa/VerkkoonTunkeutuminen/blob/main/h1_korva_netissa.md).

<br>

## b) Ei voi kalastaa

Task: Show that you can disconnect and reconnect internet connection on your Virtual Machine (Reference: Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

On Kali, disconnecting and re-connecting the network is really easy. On the taskbar in the top right there is a Network button where you can select which network the machine is connected to, including a *Disconnect*-option.

I tested the connection by pinging `ping 8.8.8.8`.

<img width="786" height="291" alt="kuva" src="https://github.com/user-attachments/assets/278ad65a-766d-42f4-a822-19013b186692" />

While the network is disconnected, the ping doesn't work:

<img width="787" height="209" alt="kuva" src="https://github.com/user-attachments/assets/902e267e-b819-4f78-9122-2d3289bb769a" />

Re-connected, ping works again:

<img width="680" height="245" alt="kuva" src="https://github.com/user-attachments/assets/c125671f-96f7-4fe7-87bb-21cde3e84ccd" />

With a Virtual Machine it can also be done by going into the Virtual Machine's settings in VirtualBox *Right click -> Settings -> Network*, and disabling the Network Adapter. Make sure there aren't any enabled adapters in the other tabs either. This can be useful as a more permanent solution if needed.

<img width="504" height="286" alt="kuva" src="https://github.com/user-attachments/assets/73755d25-636f-4821-be20-b582ea1a4a55" />

<br>

## c) Wireshark

Task: Install Wireshark and use it to capture activity. Only your own activity. Using Virtual Machine is allowed. (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

Wireshark can be installed with `sudo apt-get update` and `sudo apt-get install wireshark` (Karvinen, T. 2025a).

My Kali Linux came with Wireshark already installed:

<img width="326" height="125" alt="kuva" src="https://github.com/user-attachments/assets/d24a7ab4-9e0b-49a6-951d-e3effc903269" />

<br>

## d) Oikeesti TCP/IP

Task: Point out TCP/IP-model's 4 layers from one captured package. In addition to explanation, hightlight them in a screenshot. (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*



<img width="350" height="740" alt="TCPIP_model" src="https://github.com/user-attachments/assets/374b19cb-7b6c-4a83-9121-be54f39eb906" />

TCP/IP Model drawn by me based on (Geeksforgeeks 2026).

<br>

## e) Mitäs tuli surffattua?

Task: Open the file **surfing-secure.pcap**. Inspect it and explain what kind of capture it is, in short and in general. (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

<br>

## f) Volutary, difficult

Task: From **surfing-secure.pap**, try to solve which browser the user is using. (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

<br>

## g) 

Task: From **surfing-secure.pap**, try to solve what model NIC (Network Interface Card) the user has. (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

<br>

## h) 

Task: From **surfing-secure.pap**, try to solve what web server the user has visited. Bad news: Connection is secured with TLS-encryption. (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

<br>

## i) Analyysi

Task: Capture a small amount of your own network traffic. Analyze it and explain what happens, in as much detail as possible. (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

<br>



List of references:

Geeksforgeeks 2026. TCP/IP Model. Readable: https://www.geeksforgeeks.org/computer-networks/tcp-ip-model/. Read: 30.10.2026.

Karvinen, T. 2025a. Wireshark - Getting Started. Readable: https://terokarvinen.com/wireshark-getting-started/. Read: 29.10.2026.

Karvinen, T. 2025b. Network Interface Names on Linux. Readable: https://terokarvinen.com/network-interface-linux/. Read: 29.10.2026.

Karvinen, T. & Iso-Anttila, L. 2026. Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance. Readable: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Read: 29.10.2026.
