# h4 NFC & RFID

<br>

Work environments: Kali Linux 2026.2 Virtual Machine & Honor X6a android-phone.

As with all other weekly exercises, I started by running `sudo apt-get update && sudo apt upgrade -y` on my Virtual Machine to make sure everything is up to date.

<br>

## a) Task: Take a look at the RFID products you use, and think how well are you protected against snooping? (Karvinen & Iso-Anttila 2026)

First things that came to mind thinking about this question were the physical precautions I have taken, like using an RFID-blocking wallet and always keeping my phone's NFC-feature toggled off when not specifically in use.

I used the app **NFC TagInfo by NXP** on my android phone, which I downloaded from the Google Play store, to scan some of the cards in my use.

One card I tested was my customer loyalty card for a grocery store, and looked around a bit for some interesting information.

The physical range limit to read the card's chip was about 5 cm.

TagInfo revealed that the manufacturer was **NXP Semiconductors** and the type was **MIFARE DESFire EV1**.

The total memory size for the chip was 2 kB and available memory was 1.8 kB.

The card was manufactured in week X, 2022.

There was some information about the Android Technology and Protocol Information, as well as a list of supported technologies.

In the **Memory Content** field it displayed a text *No application information available*.

There didn't seem to be any sensitive information readable in plain text there. Still, I wasn't sure which pieces of information would've been safe to share, so I didn't attach any screenshots from the app here.

<br>

## b) Task: Familiarize yourself with the structure of APDU commands. Use of AI is permitted for this. (Karvinen & Iso-Anttila 2026)

APDU stands for Application Protocol Data Units. In a smart card conversation sequence the host sends a command APDU, and the card answers with a response APDU. The two status bytes at the end of each response tell you what happened (Albimat 2023).

<br>

## c) Task: Research and share an interesting news article regarding RFID hacking. (Karvinen & Iso-Anttila 2026)

<br>

List of references:

Albimat 2023. Smart Card APDU Commands: A Practical Developer Reference. Readable: https://ambimat.com/smart-card-selected-apdu-commands/. Read: 15.11.2026.

Karvinen, T. & Iso-Anttila, L. 2026. Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance. Readable: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Read: 14.11.2026.
