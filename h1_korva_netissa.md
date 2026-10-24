# h1 "Korva netissä"

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

<br>

## b) Moduwhat?

<br>

## c) ADS-B

<br>

## d) Atalaya (voluntary)

<br>

## e) WifiAnalyzer (voluntary)

<br>

## f) GPSTest (voluntary)


<br>

List of references:

Government of Canada 2026. Radiofrequency Energy and Safety. Readable: https://ised-isde.canada.ca/site/spectrum-management-telecommunications/en/safety-and-compliance/facts-about-towers/radiofrequency-energy-and-safety. Read: 24.10.2026.

Ghayas, A. 6.6.2021. Wavelength Calculator: Calculating wavelength of radio waves. Readable: https://commsbrief.com/wavelength-calculator-calculating-wavelength-of-radio-waves/. Read: 24.10.2026.

Karvinen, T. & Iso-Anttila, L. 2026. Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance. Readable: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Read: 24.10.2026.
