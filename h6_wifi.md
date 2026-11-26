# h6 WiFi

<br>

Before moving on to the tasks, I started by going to the course website (Karvinen & Iso-Anttila 2026) and downloading the **WiFiChallenge Lab v2.5.1.ova** file from the drive link, then imported the appliance into my Oracle VirtualBox Manager.

When starting the Virtual Machine, I got an error saying the network adapter does not exist. I clicked on change it and switched the adapter from NAT to Bridged Adapter, which fixed the issue.

<img width="383" height="253" alt="kuva" src="https://github.com/user-attachments/assets/059ddfb8-8d0a-4e16-9569-0a52932ae835" />

## a) Task: Familiarize yourself with the wifi challenge lab 2.1 exercise environment, and if necessary make use of the existing instructions (Karvinen & Iso-Anttila 2026)

I navigated to the WifiChallenge Lab website https://lab.wifichallenge.com/ and logged in using my account, then navigated to the Challenges-section.

For ease of use, I had the lab open on my host Windows PC, as it seemed like the lab only had the questions itself, while getting the answers to them relied on using the virtual machine.

I noticed the keyboard seemed to be set on US, which I changed (temporarily) to Finnish with the command `setxkbmap fi`.

I started with the introduction challenge *00. What is the contents of the file /root/flag.txt on the VM?*

Inside the VM, I used the command `cat /root/flag.txt` to print the contents of the file. I wasn't expecting it to work just like that, but I had to test it, and to my surprise it did.

<img width="429" height="68" alt="kuva" src="https://github.com/user-attachments/assets/50c82d37-be3e-4fac-a263-b0fe96346579" />

I inserted the flag **flag{2162ae75cdefc5f731dfed4efa8b92743d1fb556}** into the lab challenge and got a success.

<img width="411" height="167" alt="kuva" src="https://github.com/user-attachments/assets/091da5a9-fc37-4726-a7c3-b4536af86c50" />

The next challenge *01. What is the channel that the wifi-global Access Point is currently using?* was already a bit more challenging and I had to peek at the hints offered.

<img width="186" height="126" alt="kuva" src="https://github.com/user-attachments/assets/3b3163f3-3e48-4f29-b39a-27ce8325893c" />

I looked through the manuals with `man iw | less` and `man airodump-ng | less` for a bit but found nothing that would've led me to the solution, so I had to check the walkthrough to get started.

The walkthrough (r4ulcl 2023) suggested that we needed to first put the card in monitor mode with `airmon-ng`, then scan the channels using `airodump-ng` to find the wifi-global network.¨

Following the walkthrough, I first created a new directory `mkdir ~/wifi` as suggested, then used the command `sudo airmon-ng start wlan0` to put wlan0 in monitor mode:

<img width="828" height="517" alt="kuva" src="https://github.com/user-attachments/assets/64dfaede-ba5b-4ff3-8055-bec172f478c2" />

`sudo airodump-ng wlan0mon -w ~/wifi/scan --manufacturer --wps --band abg` to scan the channels:

<img width="1151" height="669" alt="kuva" src="https://github.com/user-attachments/assets/16a8bfee-df25-423b-9a28-71811e395336" />

44 was the correct answer.


<br>

## b) Task: Write a report about what you learned and which things surprised you as you did the exercises (Karvinen & Iso-Anttila 2026)



<br>

## c) Task: How has your attitude changed regarding WLAN security after you did the exercises? (Karvinen & Iso-Anttila 2026)



<br>

List of references:

Haaga-Helia. n.d. WIFI. Readable: https://hhmoodle.haaga-helia.fi/pluginfile.php/5055846/mod_resource/content/1/01-WIFI.pdf. Read: 27.11.2026.

Karvinen, T. & Iso-Anttila, L. 2026. Verkkoon tunkeutuminen ja tiedustelu - ICI013AS3A-3004 Tero ja Lari - ti 11:00 pa5001 - 2026p2 +vt4. Readable: https://hhmoodle.haaga-helia.fi/course/view.php?id=49869&section=1. Read: 26.11.2026.

r4ulcl 2023. Walkthrough WifiChallenge Lab v2.0. Readable: https://r4ulcl.com/posts/walkthrough-wifichallenge-lab-2.0/. Read: 27.11.2026.

WifiChallenge Lab. n.d. Challenges. Readable: https://lab.wifichallenge.com/challenges. Read: 26.11.2026.
