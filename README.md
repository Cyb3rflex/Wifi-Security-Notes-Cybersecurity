# Wifi-Security-Notes-Cybersecurity

# WiFi Security

> Concise, exam-ready, and safe overview of WiFi security concepts, common vulnerabilities, defensive controls, and ethical practice.

---

## Table of contents

* [Overview](#overview)
* [Key concepts & terminology](#key-concepts--terminology)
* [Security goals (CIA + auth/access control)](#security-goals-cia--authaccess-control)
* [Common vulnerabilities](#common-vulnerabilities)
* [High-level WiFi hacking techniques (descriptive only)](#high-level-wifi-hacking-techniques-descriptive-only)
* [Detection & monitoring](#detection--monitoring)
* [Mitigations & best practices](#mitigations--best-practices)
* [Legal & ethical considerations](#legal--ethical-considerations)
* [Safe learning & practice paths](#safe-learning--practice-paths)
* [Quick summary](#quick-summary)
* [Contributing / Edits](#contributing--edits)
* [License](#license)

---

## Overview

This README is a compact reference for WiFi security: concepts you must know, weaknesses commonly exploited, defensive controls, monitoring signals, and how to practice legally. Offensive techniques are described at a high level only — **do not** perform attacks on networks you do not own or have explicit permission to test.

## Key concepts & terminology

* **SSID:** Human-readable network name broadcast by an Access Point (AP).
* **BSSID:** MAC address of the AP radio (unique identifier for the radio).
* **Client / STA:** Any device that connects to an AP (phone, laptop, IoT).
* **802.11:** WiFi standard family (a/b/g/n/ac/ax). Defines PHY/MAC behavior.
* **Channels & bands:** 2.4 GHz, 5 GHz, 6 GHz; channels are frequency slices.
* **Authentication vs Encryption:** Authentication verifies identity (PSK, 802.1X); encryption protects frame contents (WEP, WPA, WPA2, WPA3).
* **WPA2 / WPA3:** Modern WiFi security protocols; WPA3 improves protections against certain offline attacks and handshake weaknesses.

## Security goals (CIA + auth/access control)

* **Confidentiality:** Prevent eavesdropping on wireless frames.
* **Integrity:** Prevent tampering and injection of false frames.
* **Availability:** Keep legitimate clients connected and usable (defend against jamming/DoS).
* **Authentication / Access control:** Ensure only authorized clients join the network.

## Common vulnerabilities

* **Weak/shared passphrases:** Short or guessable PSKs enable offline cracking.
* **Obsolete protocols:** WEP and TKIP have fundamental cryptographic flaws.
* **Misconfigured APs:** Default admin credentials, open management interfaces, exposed WPS.
* **Rogue APs / Evil twin:** Unauthorized APs mimicking legitimate SSIDs to capture credentials or traffic.
* **Unprotected management frames (older standards):** Allow control-frame forgeries; PMF (802.11w) mitigates this.
* **Client auto-join behavior:** Devices that auto-join remembered SSIDs or accept captive portals are higher risk.
* **Physical/RF attacks:** Jamming, deauthentication floods targeting availability.

## High-level WiFi hacking techniques (descriptive only)

> Purposefully non-actionable — conceptual categories used to understand risks and defenses.

* **Passive eavesdropping:** Listening to wireless traffic and metadata; unencrypted or weakly encrypted payloads may be readable.
* **Rogue AP / Evil twin:** Attacker advertises a familiar SSID to trick clients into connecting and capture credentials or traffic.
* **Traffic interception / MITM:** Intercepting or modifying traffic between client and network (e.g., via rogue gateway). Use end-to-end encryption to mitigate.
* **Handshake capture & offline cracking (conceptual):** Capturing WPA/WPA2 handshakes and attempting offline passphrase guesses — mitigated by strong passphrases and WPA3.
* **Deauthentication/disassociation attacks:** Forging control frames to disconnect clients (used for disruption or forcing captive-portal reconnections). PMF reduces this risk.
* **Exploitation of vendor bugs / management interfaces:** Vulnerable AP firmware or exposed admin interfaces can be exploited.
* **Traffic-analysis / side-channels:** Inferring user behavior or presence from metadata even without reading payloads.

## Detection & monitoring

Signals defenders should watch for:

* **Duplicate SSIDs / unexpected BSSIDs** — potential rogue APs.
* **New/unrecognized BSSIDs on a known SSID** — evil twin indicator.
* **Spikes of deauth/disconnect frames** — possible DoS or targeted disruption.
* **High probe request volume from clients** — devices searching for networks (privacy risk).
* **Unusual association patterns or unexpected clients** — unauthorized devices connected.
* **Rogue DHCP servers / unexpected gateway IPs** — MITM indicator.

## Mitigations & best practices

* **Use modern encryption:** WPA3 (preferred). If unavailable, use WPA2-AES with a strong passphrase.
* **Prefer 802.1X for enterprise:** RADIUS-backed authentication with unique per-user/device credentials and certificate-based EAP when possible.
* **Strong passphrases:** Long, random PSKs if PSK mode is used; rotate keys as appropriate.
* **Protect AP management plane:** Change default admin passwords, disable remote admin over WiFi, use HTTPS for management, and keep firmware updated.
* **Disable WPS:** Known to be insecure — turn it off.
* **Enable Protected Management Frames (PMF / 802.11w):** Helps prevent forged control-frame attacks.
* **Network segmentation:** Use guest VLANs for visitors and isolate IoT devices.
* **Deploy WIDS/WIPS:** Wireless intrusion detection/prevention to alert on rogue APs, jamming, or suspicious frames.
* **Client hardening:** Disable auto-join for unknown networks, use VPNs on untrusted WiFi, and keep devices patched.
* **Site survey & channel planning:** Reduce co-channel interference and improve availability.
* **Use HTTPS and certificate best practices:** Protect credentials and web traffic from interception.

## Legal & ethical considerations

* Testing, scanning, or attacking WiFi systems **without explicit written permission** is illegal in many jurisdictions.
* Follow responsible disclosure if you discover vulnerabilities in third-party equipment or services.
* Practice only in controlled labs or with explicit authorization.

## Safe learning & practice paths

* **Build isolated labs:** Use physical or virtual APs and client devices you control.
* **Use legal training platforms:** CTFs and vendor labs that provide WiFi scenarios.
* **Read standards & authoritative guidance:** IEEE 802.11 specs, NIST guidance, and vendor security docs.

## Quick summary

Use strong, modern encryption (WPA3 / 802.1X), centralize authentication where possible, harden AP management, monitor for anomalies, and practice only with permission.

---

## Contributing / Edits

Suggestions welcome. If you want this README changed to include badges, diagrams, configuration examples (defensive only), or printable cheat-sheet formats, open a PR or request changes here.

## License

This document is provided under the MIT License — feel free to use and adapt for educational purposes. See `LICENSE` for details.
