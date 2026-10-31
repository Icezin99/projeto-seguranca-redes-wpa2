# Wi-Fi Network Security Project (WPA2)

Practical project developed within the scope of the Security course of the Bachelor's Degree in Computer Engineering (Networking and Systems Administration Track) at ISEC.

## Project Overview

The main objective of this project was to study the security mechanisms and vulnerabilities associated with the WPA2-PSK protocol. The practical component consisted of executing a controlled security auditing scenario (pentest), focusing on capturing the initial authentication process and performing an offline dictionary attack to recover the password.

## Methodology and Study Phases

1. **Theoretical Foundation:** In-depth study of the WPA2 protocol, the transition from TKIP to CCMP (with AES cipher), and a detailed analysis of the four messages exchanged during the 4-Way Handshake process.
2. **Test Environment:** Configuration of an isolated lab using an Access Point (AP), a legitimate client station, and a Kali Linux virtual machine equipped with a Wi-Fi adapter supporting Monitor Mode and packet injection (RTL8821AU chipset).
3. **Monitoring and Capture:** 
   * Enabling monitor mode on the interface (`wlan0`).
   * Using `airodump-ng` for target network reconnaissance and traffic capture redirection.
   * Executing a deauthentication attack with `aireplay-ng` to force client re-authentication and capture the *4-Way Handshake* into a `.cap` file.
4. **Validation:** Inspection and isolation of EAPOL traffic in Wireshark to confirm the integrity and validity of the captured messages.
5. **Dictionary Attack (Offline):** Using the `aircrack-ng` tool combined with the global `RockYou.txt` wordlist to test candidate keys from the obtained handshake.

## Main Results

- The offline dictionary attack demonstrated high effectiveness when vulnerable credential patterns were applied. 
- The target network password (`chocolate`) was successfully recovered in just 1 second, after testing 5,979 candidate keys.
  
<p align="center">
  <img width="546" height="322" alt="key-found" src="https://github.com/user-attachments/assets/34704a1c-2d77-4d73-80e2-5673b7cbee3f" />
</p>

- The study proved that while WPA2 uses robust ciphers like AES-CCMP, network security is severely compromised if the user opts for weak passwords or ones present in public data breach lists.

## Repository Contents

- [`report/`](report/) - Complete technical report of the project in PDF format (`.pdf`).
- [`resources/`](recursos/) - Support files and resources used during the experimental demonstration.
