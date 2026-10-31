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

Reference: Karvinen 2025a

<br>

**Network Interface Names on Linux**

- Network interface is like a network card, but it's not always a physical card.
- All computers have the loopback interface for localhost, which has no physical card.
- IPv4 local addresses are 127.0.0.1/8 and IPv6 local addresses are ::1/128.
- You can check your interfaces with *ip a* (ip address) and *ip route*.

Reference: Karvinen 2025b

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

Wireshark can be installed with `sudo apt-get update` and `sudo apt-get install wireshark` (Karvinen 2025a).

My Kali Linux came with Wireshark already installed:

<img width="326" height="125" alt="kuva" src="https://github.com/user-attachments/assets/d24a7ab4-9e0b-49a6-951d-e3effc903269" />

<br>

## d) Oikeesti TCP/IP

Task: Point out TCP/IP-model's 4 layers from one captured package. In addition to explanation, hightlight them in a screenshot. (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

TCP/IP Model based on the article by Geeksforgeeks (2026):

<img width="350" height="740" alt="TCPIP_model" src="https://github.com/user-attachments/assets/374b19cb-7b6c-4a83-9121-be54f39eb906" />

I started a Wireshark recording on **any** network and navigated to www.google.com on a web browser to generate some traffic.

I used the following package as an example for this exercise:

<img width="1027" height="42" alt="kuva" src="https://github.com/user-attachments/assets/304955c8-9b12-4b23-ab57-cd9693ecdbe7" />

<img width="728" height="106" alt="kuva" src="https://github.com/user-attachments/assets/a5ea54d7-2d45-4a1a-9d16-0165ae00e623" />

Based on the used protocols, and according to IBM (2026), I combined the packet information sections from Wireshark into TCP/IP Model:

<img width="1041" height="435" alt="kuva" src="https://github.com/user-attachments/assets/38681fda-b198-4abb-a76c-909158173c8d" />

*Linux cooked capture v1* was working on the Link-layer based on the information inside the header. It's normally called *Ethernet II*, but was displayed with a different name for me possibly due to my VPN- or VirtualBox-settings.

<img width="753" height="292" alt="kuva" src="https://github.com/user-attachments/assets/669ea1cd-b3e3-41ce-afdc-478f4caa1df5" />

<br>

## e) Mitäs tuli surffattua?

Task: Open the file **surfing-secure.pcap**. Inspect it and explain what kind of capture it is, in short and in general. (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

I downloaded the file *surfing-secure.pcap* from course website (Karvinen & Iso-Anttila 2026) and opened it in Wireshark from a new terminal `wireshark ~/Downloads/surfing-secure.pcap`.

The whole capture consisted of 283 lines of traffic. Protocols included DNS, QUIC, TCP, TLSv1.3 and ARP.

The first thing I noticed the user had navigated to www.google.com and terokarvinen.com. Both included DNS queries.

<img width="1336" height="304" alt="kuva" src="https://github.com/user-attachments/assets/03e91978-9b1e-4d83-93cc-8cc71b08e5a3" />

There were also traffic to gc.zgo.at and terokarvinen.goatcounter.com. With a quick googling, GoatCounter seems to be an open source web analytics tool.

Near the end there was also an ARP request for another device on the LAN.

The whole traffic was captured on 2025-03-28 and lasted about 7.5 seconds.

<br>

## f) Volutary, difficult

Task: From **surfing-secure.pap**, try to solve which browser the user is using. (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

I tried inspecting namely the Client Hello -packages, which can be viewed easier by applying the filter `tls.handshake.type == 1`, for a bit. I didn't however find anything that would lead me to the path of finding out which browser was used here.

Next thing I did was I asked ChatGPT-6 LLM to analyze the file, try to solve the issue and explain to me how the conclusion was reached:

Client Hello is sent by the browser to the server when the HTTPS connection is established. The message contains information about the client's TLS implementation like supported encryption algoritms and extensions.

I used this package for inspection:

<img width="996" height="26" alt="kuva" src="https://github.com/user-attachments/assets/c5e756b3-6a0e-422b-b1a1-88aecca5cc39" />

Under *Transport Layer Security* -> *TLSv1.3 Record Layer: Handshake Protocol: Client Hello* -> *Handshake: Client Hello* -> *Cipher Suites (17 suotes)* I found the following cipher suites:

<img width="672" height="317" alt="kuva" src="https://github.com/user-attachments/assets/6c7a1a4c-3816-4d8d-b273-e84c2b45099e" />

Different browsers and TLS implementations have different preferences for encryption algorithms, and the order can help distinguish them also.

On the very bottom of *Handshake Protocol: Client Hello* I found the following line *[JA3: b5001237acdf006056b409cc433726b0]*:

<img width="738" height="106" alt="kuva" src="https://github.com/user-attachments/assets/f106490b-9763-4039-b50d-8bad2b4afeac" />

Pasting this fingerprint into a [JA3 Database](https://ja3.zone/) (JA3.ZONE), the overwhelming majority of the results were Firefox, with a few Chrome and one Opera.

<img width="1367" height="630" alt="kuva" src="https://github.com/user-attachments/assets/4cdd6048-87f8-498d-a388-13dd050be230" />

This leads me to strongly believe the client in the capture was using Mozilla Firefox browser, but I couldn't find anything that would prove it 100% guaranteed.

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

ChatGPT-6 LLM .

IBM 2026. TCP/IP Protocols and Functions. Readable: https://www.ibm.com/docs/en/zvm/7.4.0?topic=protocols-tcpip-functions. Read: 31.10.2026.

JA3.ZONE. TLS Fingerprint Database. Readable: https://ja3.zone/. Read: 31.10.2026.

Karvinen, T. 2025a. Wireshark - Getting Started. Readable: https://terokarvinen.com/wireshark-getting-started/. Read: 29.10.2026.

Karvinen, T. 2025b. Network Interface Names on Linux. Readable: https://terokarvinen.com/network-interface-linux/. Read: 29.10.2026.

Karvinen, T. & Iso-Anttila, L. 2026. Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance. Readable: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Read: 29.10.2026.
