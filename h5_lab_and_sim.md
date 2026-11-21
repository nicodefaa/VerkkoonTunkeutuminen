# h5 Laboratorio- ja simulaatioympäristöt hyökkäyksissä / Lab- and simulation environments in attacks

<br>

Work environment: Kali Linux 2026.2 Virtual Machine

As with all other weekly exercises, I started by running `sudo apt-get update && sudo apt upgrade -y` on my Virtual Machine to make sure everything is up to date.

<br>

## a) Task: Run the  ARP attack presented at the class, and research how it works (Karvinen & Iso-Anttila 2026b).

I wasn't able to be present at this week's class, but I found the material on the course's Moodle-page (Karvinen & Iso-Anttila 2026a).

I started by downloading the files from the OneDrive-link provided in the coursepage:

<img width="430" height="153" alt="kuva" src="https://github.com/user-attachments/assets/dfd120b4-4e7f-4005-8a31-5a2359c2c13f" />

I registered as new user on [WMWare](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion) and downloaded the **VMware Workstation Pro (For Windows) 26H1u1**.

<img width="941" height="430" alt="kuva" src="https://github.com/user-attachments/assets/67c6cb6f-4470-49bc-a82d-b9eedbe8d7c7" />

File -> Open -> mininet-2.3.0-210211-ubuntu-20.04.1-legacy-server-amd64-Student-lab.vmdk -> Power on this virtual machine, gave me the following error:

<img width="1138" height="253" alt="kuva" src="https://github.com/user-attachments/assets/33770acd-d8e7-4641-a0d3-e57861a281fe" />

I clicked browse, and selected the file .vmdk file again:

<img width="887" height="276" alt="kuva" src="https://github.com/user-attachments/assets/4bc75033-9326-46d7-80b5-5f81013c1fc9" />

Clicking on "I copied it" gave me another error:

<img width="1090" height="339" alt="kuva" src="https://github.com/user-attachments/assets/fd3da09e-2805-42cf-8b25-dec55bf55650" />

I also tried to re-download the files from OneDrive (which was also very slow for some reason), but the same problem persisted.

After a bit of troubleshooting, I noticed the files in the folder were all less than 1 mb in size, which meant something had probably gone wrong in the download or extraction.

I tried unzipping the **mininet-2.3.0-210211-ubuntu-20.04.1-legacy-server-amd64-Student-lab.tar.xz** found inside the directory. While unzipping it asked if I wanted to replace some files, which I answered no to for all. 

Now I was able to boot up the virtual machine:

<img width="555" height="143" alt="kuva" src="https://github.com/user-attachments/assets/3590fa44-69c3-414b-89aa-373f33c7491b" />

I used the default credentials **mininet mininet** to log in.

<img width="746" height="244" alt="kuva" src="https://github.com/user-attachments/assets/79782eaf-e1e9-4fc1-b51e-bd126a58b566" />

Now it was time to try out the ARP attack. I found the guide to this starting from page 17 in 03-mininet.pdf (Haaga-Helia n.d.).

The VM layout was set to US as a default, which made it harder to input the required commands. I asked Copilot how I could change it, and it gave me the command to use `sudo dpkg-reconfigure keyboard-configuration` after this I could select the new language layout:

<img width="583" height="298" alt="kuva" src="https://github.com/user-attachments/assets/f7dfe843-8ad7-425a-878b-ceb9e8daea0b" />

Rest of the options I went with defaults. Afterwards I used `sudo service keyboard-setup restart` to make the change come into effect.

As instructed in the guide (Haaga-Helia n.d.), I used the first command `ryu-manager ryu.app.simple_switch_13`:

<img width="524" height="126" alt="kuva" src="https://github.com/user-attachments/assets/5298b19e-9851-41b2-a965-33de4bfe9d7d" />

That command occupied the terminal which didn't let me input any other commands. I asked Copilot again for help, and it told me to open a new terminal with **alt+F2**, and switch between with **alt+F1** and **alt+F2**. I logged into the new terminal and used the second command `sudo mn --topo single,3 --mac --switch ovsk --controller remote` instructed in the guide:

<img width="703" height="302" alt="kuva" src="https://github.com/user-attachments/assets/770d7848-54f7-4b05-a5a9-954655826e01" />

Next, the `pingall` command:

<img width="323" height="120" alt="kuva" src="https://github.com/user-attachments/assets/81d517e7-45ce-4fea-b0f9-293f910e15f6" />

The next instructed command `xterm h1` did not work however:

<img width="320" height="97" alt="kuva" src="https://github.com/user-attachments/assets/2f34a01e-a563-45ca-89a9-f14cb6d15693" />

The guide told me to run `./get_xauth.sh` if there were issues with xterm, but this was not a recognized command either:

<img width="296" height="93" alt="kuva" src="https://github.com/user-attachments/assets/b2dcfe1f-0feb-4ef8-871a-e6eff951aa1f" />

I asked about this error from Copilot that explained me that this command tried to open a graphical terminal window, while my VM was running a text-only console. It told me that they corresponding commands to use in TTY console would be `h1 ping h2`, `h1 ifconfig` and `h1 arp -n`, which I tested:

<img width="549" height="352" alt="kuva" src="https://github.com/user-attachments/assets/3847fcd4-bbc4-498b-aa04-e0ba0ffb3970" />

<img width="579" height="274" alt="kuva" src="https://github.com/user-attachments/assets/f7a79437-5c32-4845-a333-ef7175cd4b62" />

<img width="678" height="77" alt="kuva" src="https://github.com/user-attachments/assets/5417137a-9609-4e3e-8503-6d1147e68ff8" />

Then the next commands instructed in the guide, used with the `h3` prefix since xterm didn't work for me, `sysctl -w net.ipv4.ip_forward=1`, `iptables -t nat -A PREROUTING -p tcp --dport 22 -j REDIRECT --to-
port 22` and `tcpdump -i h3-eth0 -w arp-p.pcap &`:

<img width="364" height="39" alt="kuva" src="https://github.com/user-attachments/assets/a8cf7eb1-16c9-4e93-bcc6-eba0737ed71a" />

<img width="691" height="41" alt="kuva" src="https://github.com/user-attachments/assets/0da6e68b-2266-4e4a-a738-391b3bd0d612" />

<img width="385" height="74" alt="kuva" src="https://github.com/user-attachments/assets/b3e09880-3729-436e-bb0d-758312311a95" />

`h3 wireshark &`:

<img width="695" height="39" alt="kuva" src="https://github.com/user-attachments/assets/ff15f011-37f6-41c9-b7c2-8cb1dd2fa530" />

`sshesame -port 22 -listen_address 0.0.0.0`:

<img width="820" height="88" alt="kuva" src="https://github.com/user-attachments/assets/e1746fb4-bfa1-489e-8e5c-b6ec905bfa9e" />

`python3 ./arp_poison.py` ran into another issue:

<img width="748" height="212" alt="kuva" src="https://github.com/user-attachments/assets/132518ee-b41e-47ad-9f4a-2f2825be4cbc" />

At this point I had spent several hours troubleshooting various issues and was running low on time, so I had to concede that this task was too hard for me with the given instructions. I had either done something wrong during the installation process or the instructions weren't matching the virtual machine that was provided.

<br>

## b) Task: In the same directory there's also ICMP Spoofing and TCP Session Hijacking, run both labs and explain how each technique works (Karvinen & Iso-Anttila 2026b).

<br>

## c) Task: In the directory 02-SDN-DDos_Simulation tryout-folder there are tools for running TCP SYN-Flood attack safely. Explain how you ran the attack and how it progresses (Karvinen & Iso-Anttila 2026b).

<br>

List of references:

Copilot LLM used to assist with mininet errors and commands.

Haaga-Helia n.d. Network Protocols and Vulnerabilities. Readable: https://hhmoodle.haaga-helia.fi/pluginfile.php/5055842/mod_resource/content/1/03-mininet.pdf. Read: 21.11.2026.

Karvinen, T. & Iso-Anttila, L. 2026a. Verkkoon tunkeutuminen ja tiedustelu - ICI013AS3A-3004 Tero ja Lari - ti 11:00 pa5001 - 2026p2 +vt4. Readable: https://hhmoodle.haaga-helia.fi/course/view.php?id=49869. Read: 21.11.2026.

Karvinen, T. & Iso-Anttila, L. 2026b. Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance. Readable: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Read: 21.11.2026.
