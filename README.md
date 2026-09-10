# LetLeeIn Releases

This public repository contains credential-free release binaries and SHA-256 checksums for the LetLeeIn endpoint agent. The private source, build configuration, security design, and deployment infrastructure remain in `Joleeconsultants/LetLeeIn`.

## Downloads and signatures

Use the [latest published release](https://github.com/Joleeconsultants/LetLeeIn-Releases/releases/latest) and its accompanying SHA-256 files. Current Windows releases use trusted, timestamped Authenticode signatures from Jolee Consultants LTD. The Linux administrator CLI has a SHA-256 checksum; it does not use Windows Authenticode.

Releases are published only by the private repository's GitHub Action. It builds and verifies the artifacts, signs Windows binaries, generates checksums after signing, and publishes the approved assets here. Legacy `agent-v0.1.0` predates signing enforcement and must not be represented as a signed release.

## Optional microphone forwarding component

LetLeeIn 0.6.1 adds native setup support for the optional **base VB-CABLE** virtual audio component by VB-Audio. It is proprietary donationware, not open source. Installing or upgrading LetLeeIn does not automatically install VB-CABLE, and capturing PC sound does not require it.

A compatible Jolee Remote viewer provides an explicit **Setup** action in the microphone/audio panel. Setup runs through the existing Windows service, preserves audio defaults and configured endpoint pairs, reuses a compatible installed component, and reports conflicts rather than replacing an unknown installation. It requires Windows 10 build 16299 or later on x64. A restart may be required; LetLeeIn does not restart the PC automatically.

After the remote PC confirms readiness, enable microphone forwarding separately and allow browser microphone access. Select **CABLE Output** as the microphone in the destination Windows application when needed. Setup never automatically starts capture. The native component requests a Windows notification when received audio first starts forwarding; notification settings may suppress it. The matching viewer/controller integration and live-device acceptance are tracked separately from the native release.

The origin of VB-CABLE: <https://www.vb-cable.com/>.

VB-CABLE is a donationware, all participations are welcome.

[Donate / pay](https://shop.vb-audio.com/en/win-apps/11-vb-cable.html) · [VB-Audio licensing terms](https://vb-audio.com/Services/licensing.htm)

Professional deployments where employees cannot see VB-CABLE and pay require volume licensing under the vendor terms. This feature uses the base component only, not VB-CABLE A+B or C+D.

## Enrollment

Release assets never contain customer identifiers, device credentials, enrollment codes, logs, command results, or private source code. Client enrollment is generated separately through the Cloudflare Access-protected LetLeeIn portal.
