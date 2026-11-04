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

Task: Install rtl_433 for the automatic analysis. Test that you can run it. "./rtl_433" responds "rtl_433 version 25.02 branch..." (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

I installed rtl_433 with `sudo apt install rtl_433`.

My installation went into */usr/bin/*. Running either `/usr/bin/rtl_433` or just `rtl_433` responded with the version.

<img width="589" height="206" alt="kuva" src="https://github.com/user-attachments/assets/cbdebb7b-101a-40c5-b204-9c7ab607b248" />

This was not 1:1 with how the assignment explained it, as the `./rtl-433` command did not work because the installation didn't go into current directory (home), and the response didn't include "branch...", but it seemed to work still.

The line **[SDR] No supported devices found.** just means I didn't have any compatible SDR receiver attached to my machine.

<br>

## c) Automaattinen analyysi (automatic analysis)

Task: Analyze the file and explain what happens in the recording. What signatures (e.g. id) can you find? (Karvinen & Iso-Anttila 2026) *Translated from Finnish by me.*

I downloaded the file **Converted_433.92M_2000k.cs8** from the course page (Karvinen & Iso-Anttila 2026), then ran it with `rtl_433 [filename]`:

<img width="830" height="253" alt="kuva" src="https://github.com/user-attachments/assets/a2e00ebc-bf17-4e4c-886e-80feef9f7799" />

The result was a list of 12 recordings:

<img width="885" height="697" alt="kuva" src="https://github.com/user-attachments/assets/97455cb3-0e7d-42b7-90ff-f40fc9a6c48c" />

Each one of them has the same id **8785315**


<br>

## d) Too complex 16?

<br>¨

## e) Ultimate

<br>

## f) Yleiskuva

<br>

## g) Bittistä

<br>

## h) Sdr++ *(voluntary)*

<br>

## i) GNU Radio *(voluntary)*

<br>

List of references:

Cornelius 2022. Decode 433.92 MHz weather station data. Readable: https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html. Read: 4.11.2026.

Hubacek 2019. Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs. Video (3:20-8:00). Watchable: https://www.youtube.com/watch?v=sbqMqb6FVMY. Watched: 4.11.2026.

Karvinen, T. & Iso-Anttila, L. 2026. Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance. Readable: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Read: 4.11.2026.

Lohner 2019. Decoding ASK/OOK_PPM Signals with URH and rtl_433. Readable: https://github.karllohner.com/SDR/Decoding/Example_2019-01-24/. Read: 4.11.2026.
