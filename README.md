# LetLeeIn Releases

This public repository contains credential-free release binaries and SHA-256 checksums for the LetLeeIn endpoint agent. The private source, build configuration, security design, and deployment infrastructure remain in `Joleeconsultants/LetLeeIn`.

## Downloads and signatures

Use the [latest published release](https://github.com/Joleeconsultants/LetLeeIn-Releases/releases/latest) and its accompanying SHA-256 files. Current Windows releases use trusted, timestamped Authenticode signatures from Jolee Consultants LTD. The Linux administrator CLI has a SHA-256 checksum; it does not use Windows Authenticode.

Releases are published only by the private repository's GitHub Action. It builds and verifies the artifacts, signs Windows binaries, generates checksums after signing, and publishes the approved assets here. Legacy `agent-v0.1.0` predates signing enforcement and must not be represented as a signed release.

## Included microphone forwarding component

LetLeeIn 0.6.4 includes the **base VB-CABLE** virtual audio component by VB-Audio. It is proprietary donationware, not open source. Installing or upgrading LetLeeIn includes the unchanged vendor package and prepares the component automatically. Capturing PC sound does not require it.

There is no separate Setup button. Headless preparation runs through the existing Windows service after successful agent installation, preserves audio defaults and configured endpoint pairs, reuses a compatible installed component, and reports conflicts rather than replacing an unknown installation. It requires Windows 10 build 16299 or later on x64. A restart may be required; LetLeeIn does not restart the PC automatically. If there is no single active logged-in user, preparation waits automatically so that user audio defaults can be protected.

After the remote PC confirms readiness, press the existing microphone button and allow browser microphone access. Select **CABLE Output** as the microphone in the destination Windows application when needed. Installation never automatically starts capture. The first use of VB-CABLE for PC sound or the first microphone activation opens one shared explanation, whichever happens first. It is automatically remembered for that Windows user, with no checkbox and no repeat in later sessions. The corrected 0.6.4 notice includes the vendor origin, donationware statement, payment link and licensing link. Users who saw an earlier incomplete notice see this corrected notice once. A tray indicator follows microphone forwarding; Windows may place it in tray overflow. Installation alone and PC sound captured from a physical audio endpoint do not trigger the notice.

VB-CABLE remains installed and visible in the Windows sound-device list between sessions, even on PCs with physical audio hardware. The CABLE Input entries are virtual outputs used to feed CABLE Output for applications; they are not physical speakers. Remote forwarding stops when the session ends. Keep the normal speakers selected for ordinary PC playback.

On Windows build 20348 and later, microphone forwarding is excluded from PC-sound return while other application audio remains available. Older Windows builds retain endpoint loopback and do not provide this process-based isolation.

Missing audio endpoints are rechecked after component preparation. If enabled PC sound failed because no render endpoint existed, it retries once when preparation reports ready. Windows restart-required status is reserved for installer results that request a restart; unavailable session endpoints alone do not mean a restart is required.

The origin of VB-CABLE: <https://www.vb-cable.com/>.

VB-CABLE is a donationware, all participations are welcome.

[Donate / pay](https://shop.vb-audio.com/en/win-apps/11-vb-cable.html) · [VB-Audio licensing terms](https://vb-audio.com/Services/licensing.htm)

Professional deployments where employees cannot see VB-CABLE and pay require volume licensing under the vendor terms. This feature uses the base component only, not VB-CABLE A+B or C+D.

## Remote printing

LetLeeIn prepares a persistent **Jolee Remote Print** queue using the Windows Microsoft Print to PDF driver. Forwarding is available only during an authorized remote session. The queue stays installed between sessions, with forwarding disabled. Existing default printers are preserved when known; conflicting queues are reported instead of overwritten.

## Enrollment

Release assets never contain customer identifiers, device credentials, enrollment codes, logs, command results, or private source code. Client enrollment is generated separately through the Cloudflare Access-protected LetLeeIn portal.
