# LetLeeIn Releases

This public repository contains credential-free release binaries and SHA-256 checksums for the LetLeeIn endpoint agent. The private source, build configuration, security design, and deployment infrastructure remain in `Joleeconsultants/LetLeeIn`.

## Downloads and signatures

Use the [latest published release](https://github.com/Joleeconsultants/LetLeeIn-Releases/releases/latest) and its accompanying SHA-256 files. Current Windows releases use trusted, timestamped Authenticode signatures from Jolee Consultants LTD. The Linux administrator CLI has a SHA-256 checksum; it does not use Windows Authenticode.

Releases are published only by the private repository's GitHub Action. It builds and verifies the artifacts, signs Windows binaries, generates checksums after signing, and publishes the approved assets here. Legacy `agent-v0.1.0` predates signing enforcement and must not be represented as a signed release.

## Included microphone forwarding component

LetLeeIn 0.6.2 includes the **base VB-CABLE** virtual audio component by VB-Audio. It is proprietary donationware, not open source. Installing or upgrading LetLeeIn includes the unchanged vendor package and prepares the component automatically. Capturing PC sound does not require it.

There is no separate Setup button. Headless preparation runs through the existing Windows service after successful agent installation, preserves audio defaults and configured endpoint pairs, reuses a compatible installed component, and reports conflicts rather than replacing an unknown installation. It requires Windows 10 build 16299 or later on x64. A restart may be required; LetLeeIn does not restart the PC automatically. If there is no single active logged-in user, preparation waits automatically so that user audio defaults can be protected.

After the remote PC confirms readiness, press the existing microphone button and allow browser microphone access. Select **CABLE Output** as the microphone in the destination Windows application when needed. Installation never automatically starts capture. The first microphone activation per remote session opens an explanation. Select **Don't show this again** and press OK to remember that choice for the current Windows user. Closing or acknowledging without selecting it keeps notices enabled for future sessions. A tray indicator follows microphone forwarding independently of the preference; Windows may place it in tray overflow. Reconnects and repeated toggles do not repeat the notice in the same session. The matching viewer/controller integration and live-device acceptance are tracked separately from the native release.

The origin of VB-CABLE: <https://www.vb-cable.com/>.

VB-CABLE is a donationware, all participations are welcome.

[Donate / pay](https://shop.vb-audio.com/en/win-apps/11-vb-cable.html) · [VB-Audio licensing terms](https://vb-audio.com/Services/licensing.htm)

Professional deployments where employees cannot see VB-CABLE and pay require volume licensing under the vendor terms. This feature uses the base component only, not VB-CABLE A+B or C+D.

## Enrollment

Release assets never contain customer identifiers, device credentials, enrollment codes, logs, command results, or private source code. Client enrollment is generated separately through the Cloudflare Access-protected LetLeeIn portal.
