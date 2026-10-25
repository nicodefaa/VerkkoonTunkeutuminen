# h1 "Korva netissä"  -- Nico Defaa

With this being the first exercise of this particular course, I started by downloading a new Kali linux virtual machine (version 2026.2) from [Kali's homepage](https://www.kali.org/get-kali/#kali-installer-images). I used mostly default settings and options for the installation (apart from language settings). After installation I updated and downloaded newest packages with `sudo apt-get install && sudo apt upgrade` and downloaded *micro* and *tree* with `sudo apt install micro tree`.

Work environment: Kali Linux 2026.2 Virtual Machine

<br>

## x) Spektrini - Electromagnetic spectrum

Task: Draw an electromagnetic spectrum, a line where frequency increases. Add 3-10 applications that can be very basic. Mark with arrows in which directions wavelength, antenna size, permeability, and ability to move information, increase (Reference: Karvinen & Iso-Anttila 2026). Translated from Finnish by me.

<img width="790" height="482" alt="spectrum graph image" src="https://github.com/user-attachments/assets/ee4974d1-3d85-44a5-aa4c-4687a51be89e" />

*Graph is indicative, not measured to be exact in terms of where appliances are positioned in proportion to wavelength.*

Application frequencies based on graph from (Government of Canada 2026).

Wavelength and antenna size decrease as frequency and speed (ability to move information) increase. Permeability depends more on other factors such as environment.

<br>

## a) WebSDR.

Task: Remotely use a WebSDR-radio that is in another country and listen to the transmission. Use a public radio broadcast as the example and tell the frequency, wavelength and modulation used. (Reference: Karvinen & Iso-Anttila 2026). Translated from Finnish by me.

For this task I used the web service http://websdr.org/ to find a suitable receiver to listen with. 

I found a receiver based in Milford, Pennsylvania http://websdr.k3fef.com:8901/ and found a radio on **frequency 770 kHz** and **AM modulation**, which I googled to be WABC New York City radio broadcast. At the time I was listening there was a host talking about the beautiful weather on the East Coast, then moving onto discussion about the gas prices and American economy. Around 7 pm CEST. 

<img width="1193" height="441" alt="kuva" src="https://github.com/user-attachments/assets/f73c1a04-a069-4fca-9e30-3ea047637bbe" />

The wavelength of radio wave is calculated by dividing the velocity (c) of the radio wave by frequency (f). Velocity is the speed of light 299 792 458 m/s. (Ghayas 2021)

I used the [Wavelength calculator](https://commsbrief.com/wavelength-calculator-calculating-wavelength-of-radio-waves/) on commsbrief.com to do this calculation for the wavelength for the example I frequency I used here, 770 kHz (0.77 MHz):

<img width="424" height="421" alt="kuva" src="https://github.com/user-attachments/assets/4677f661-04d8-4102-9c0a-65f6455064c5" />

As a result, the wavelength of the frequency 770 kHz is **389 meters** (rounded down from 389.34085454545453).

<img width="1057" height="511" alt="kuva" src="https://github.com/user-attachments/assets/4b8316d1-96ff-40d0-990b-0475af1066f5" />


<br>

## b) Moduwhat?

Task: Listen to a channel that is using a different modulation from the one used previously (Reference: Karvinen & Iso-Anttila 2026). Translated from Finnish by me.

My previous channel was using the AM modulation. First I tried to look through receivers for a FM channel, but it was hard to find one with good signal / audio quality.

Searching through a little more I found on the receiver http://sdrgeorgia.sytes.net:8902/ a LSB modulation channel on frequency 3679.00 kHz.

I heard some people talking with each other in a foreign language (possibly russian?).

<img width="1057" height="511" alt="kuva" src="https://github.com/user-attachments/assets/623d0001-007d-4a44-9505-ae52e26c3b8a" />


<br>

## c) ADS-B

Task: Find a plane that interests you from the ADS-B Exchange -service. Describe the plane and its flight and how you found the information (Reference: Karvinen & Iso-Anttila 2026). Translated from Finnish by me.

I navigated to the address https://www.adsbexchange.com/ and clicked *View the map* on the top right. 

I clicked one one of the planes on the map which was a UAL3865 United Airlines type B789 commercial plane. Having it selected it showed the flown path on the map and a side panel with other information like speed, altitude, position coordinates.

It had left from the Detroit International Airport at 19:25 UTC and was currently flying over Baca County at 37100 ft altitude.

<img width="376" height="444" alt="kuva" src="https://github.com/user-attachments/assets/bea81144-63ce-497a-93e7-307e3fa8fbef" />

<img width="185" height="136" alt="kuva" src="https://github.com/user-attachments/assets/140bb2b7-6d83-4a06-bdf0-cd5856006d5f" />

<img width="341" height="354" alt="kuva" src="https://github.com/user-attachments/assets/b903261f-fc72-4382-9839-3c6c07273673" />


<br>

## d) Atalaya (voluntary)

Task: Install F-Droid, and Atalaya with it. Use the app and explain results (Reference: Karvinen & Iso-Anttila 2026). Translated from Finnish by me.

On my Android phone (Honor x6a), I navigated to the site https://f-droid.org/ using a web browser (I used Brave), and downloaded the F-Droid.apk installation file. From the downloads directly I ran the file with my phone's built-in packet installer.

After installing I opened the F-Droid app and searched for *Atalaya*. After installation opening the app provided the following view on the Monitor-tab:

<img width="720" height="1612" alt="atalaya_1" src="https://github.com/user-attachments/assets/62e58061-687e-4b41-b107-2967b91bbbc4" />

*Some information censored by me for privacy reasons.*

I asked Copilot to explain the information seen on the screen. Here are the explanations it told me, starting from top, left to right:

Telia = operator

4G LTE = connection technology

2600 = LTE frequency in MHz

CI = Complete LTE cell identity (number sequence)

TAC = Tracking area code (number sequence)

eNB = base station / tower identifier (number sequence)

PCI = Physical cell ID used by radio network (number sequence)

CID = sector/ cell on the tower (number)

Signals:

RSRP -89.0 dBm = signal strength

RSRQ -9 dB = signal quality

SNR 25 dB = signal-to-noise ratio


Copilot also provided me with the following reference values:

RSRP: -80 dBm = excellent, -110 dBM = weak (-89 dBm = good)

RSRQ: -3 dB to - 8 dB = excellent, -11 to 15 dB = poor (-9 dB = good)

SNR: 20 dB = excellent, <10 dB = poor (25 dB = excellent)



Reference: M365 Copilot.

<br>

## e) WifiAnalyzer (voluntary)

Task: Install WifiAnalyzer with F-Droid, use the app and explain results (Reference: Karvinen & Iso-Anttila 2026). Translated from Finnish by me. 

<br>

## f) GPSTest (voluntary)

Task: Install GPSTest with F-Droid, use the app and explain results (Reference: Karvinen & Iso-Anttila 2026). Translated from Finnish by me. 


<br>

List of references:

Government of Canada 2026. Radiofrequency Energy and Safety. Readable: https://ised-isde.canada.ca/site/spectrum-management-telecommunications/en/safety-and-compliance/facts-about-towers/radiofrequency-energy-and-safety. Read: 24.10.2026.

Ghayas, A. 6.6.2021. Wavelength Calculator: Calculating wavelength of radio waves. Readable: https://commsbrief.com/wavelength-calculator-calculating-wavelength-of-radio-waves/. Read: 24.10.2026.

Karvinen, T. & Iso-Anttila, L. 2026. Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance. Readable: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Read: 24.10.2026.

M365 Copilot GPT-5 chat model was used to explain and assist using the apps on tasks d, e and f.
