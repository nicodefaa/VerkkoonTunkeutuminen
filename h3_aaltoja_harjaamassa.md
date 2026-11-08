# h3 Aaltoja harjaamassa  - Nico Defaa

<br>

Work environment: Kali Linux 2026.2 Virtual Machine

As with all other weekly exercises, I started by running `sudo apt-get update && sudo apt upgrade -y` on my Virtual Machine to make sure everything is up to date.

<br>

## x) Read and summarize

### Universal Radio Hacker SDR

- Universal Radio Hacker is a tool that can be used to record and analyze radio wave signals in a visual interface.
- Choosing the right frequency and modulation for the scanned device is important.
- For the remote in the video the frequency used was 433,745MHz and modulation was ASK (Amplitude Shift Keying).
- Bit Length should be close to the microsecond amount on the smallest part of the message.

Reference: Hubacek 2019.

### Decode 433.92MHz weather station data

- RTL-SDR is a small receiver device that can be used to capture radio signals.
- In URH, the device (RTL-SDR) should be selected from the Spectrum Analyzer where you can visually confirm the presence of signal and the real frequency.
- In URH, you can create projects, record signals and save the results.

Reference: Cornelius 2022.

<br>

**a) missing in the assignments*

## b) rtl_433

Task: Install rtl_433 for the automatic analysis. Test that you can run it. "./rtl_433" responds "rtl_433 version 25.02 branch..." (Karvinen & Iso-Anttila 2026). *Translated from Finnish by me.*

I installed rtl_433 with `sudo apt install rtl_433`.

My installation went into */usr/bin/*. Running either `/usr/bin/rtl_433` or just `rtl_433` responded with the version.

<img width="589" height="206" alt="kuva" src="https://github.com/user-attachments/assets/cbdebb7b-101a-40c5-b204-9c7ab607b248" />

This was not 1:1 with how the assignment explained it, as the `./rtl-433` command did not work because the installation didn't go into current directory (home), and the response didn't include "branch...", but it seemed to work still.

The line **[SDR] No supported devices found.** just means I didn't have any compatible SDR receiver attached to my machine.

<br>

## c) Automaattinen analyysi (automatic analysis)

Task: Analyze the file and explain what happens in the recording sample. What signatures (e.g. id) can you find? (Karvinen & Iso-Anttila 2026). *Translated from Finnish by me.*

I downloaded the file **Converted_433.92M_2000k.cs8** from the course page (Karvinen & Iso-Anttila 2026), then ran it with `rtl_433 [filename]`:

<img width="830" height="253" alt="kuva" src="https://github.com/user-attachments/assets/a2e00ebc-bf17-4e4c-886e-80feef9f7799" />

The result was a list of 12 signal results:

<img width="885" height="697" alt="kuva" src="https://github.com/user-attachments/assets/97455cb3-0e7d-42b7-90ff-f40fc9a6c48c" />

Each one of them had the same id / House Code **8785315**. All the *Proove-Security* and *Nexa-Security* ones had the channel 3. The *KlikAanKlikUit-Switch* seems to be some sort of remote that sends a signal multiple times, possibly due to possible errors in some of them.

The whole recording happens within 0.4 seconds.

<br>

## d) Too complex 16?

Task: "You've recorded a sample with URH-program in .complex16s -fileform. Convert the sample into a rtl_433 compatible form and analyze it (Karvinen & Iso-Anttila 2026). *Translated from Finnish by me.*

I downloaded the file **Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s** from the course page (Karvinen & Iso-Anttila 2026). The file seemed to open fine on rtl_433:

<img width="1113" height="463" alt="kuva" src="https://github.com/user-attachments/assets/c512e7ed-7281-4990-9223-9d945c0eb31f" />

But maybe it didn't display it correctly since the task explicitly said to convert it into a compatible form...

I asked ChatGPT-6.0 LLM about this, and it said that the conversion in Kali can simply be done with the `mv` or `cp` command.

So I tried it out, and used the command `cp Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.cs8` to copy (convert) the file into another format and keep the original just in case.

<img width="1050" height="194" alt="kuva" src="https://github.com/user-attachments/assets/ae9ff082-8895-402a-8006-8d38ecd4f96e" />

Running the converted/copied .cs8 file:

<img width="979" height="739" alt="kuva" src="https://github.com/user-attachments/assets/45ed6a92-0ef2-4634-97b1-3d2e8a3cae98" />

There was no difference between the rtl_433 outputs of the .cs8 and the .complex16s files, so either the conversation didn't work properly, or it was already compatible.

According to rtl_433 documentation on github (Larsson 2026), `.cs8` and `.complex16s` are aliases for the same format. So I assumed that the file was compatible all along and it was either an error (or a trick) in the assignment.

I decided to continue analyzing the original file `rtl_433 ~/Downloads/Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s`:

<img width="999" height="738" alt="kuva" src="https://github.com/user-attachments/assets/83ccf560-89a1-4968-a959-1022ca00d53e" />

Doing a two terminal side-by-side comparison between this one and the one analyzed in task C, they seemed to be exactly identical.

<br>

## e) Ultimate

Task: Install URH, the Ultimate Radio Hacker (Karvinen & Iso-Anttila 2026). *Translated from Finnish by me.*

Following the official URH installation guide on github (Pohl 2025), I used the command `pipx install urh` to install URH.

<img width="450" height="121" alt="kuva" src="https://github.com/user-attachments/assets/e8f02a3d-c5d3-45d9-92d9-ac7e96f627b0" />

With the command `urh`, the graphical interface of the program opened:

<img width="1219" height="739" alt="kuva" src="https://github.com/user-attachments/assets/e143e478-7fc2-4f48-ae6b-9a39af432d12" />

<br>

## f) Yleiskuva

Task: Inspect the sample file. It has a recording of Nexa's power outlet remote light 1 ON -button pressed thrice. Use URH. Describe it in general, how long, what frequency, when it was recorded, how does it look in general? (Karvinen & Iso-Anttila 2026). *Translated from Finnish by me.*

<br>

## g) Bittistä

Task: Same file as in f. Demodulate the signal to get raw bits. What is the correct modulation? How long is one raw bit in real time? Describe by comparing it to something. (Karvinen & Iso-Anttila 2026). *Translated from Finnish by me.*

<br>


List of references:

ChatGPT-6.0 LLM used in task d.

Cornelius 2022. Decode 433.92 MHz weather station data. Readable: https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html. Read: 4.11.2026.

Hubacek 2019. Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs. Video (3:20-8:00). Watchable: https://www.youtube.com/watch?v=sbqMqb6FVMY. Watched: 4.11.2026.

Karvinen, T. & Iso-Anttila, L. 2026. Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance. Readable: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Read: 4.11.2026.

Larsson, B. 2026. Introduction to I/Q formats. Readable: https://github.com/merbanan/rtl_433/blob/master/docs/IQ_FORMATS.md. Read: 4.11.2026.

Lohner 2019. Decoding ASK/OOK_PPM Signals with URH and rtl_433. Readable: https://github.karllohner.com/SDR/Decoding/Example_2019-01-24/. Read: 4.11.2026.

Pohl, J. 2025. urh github repository README.md. Readable: https://github.com/jopohl/urh. Read: 4.11.2026.
