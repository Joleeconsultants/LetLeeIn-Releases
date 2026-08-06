# LetLeeIn Releases

This public repository contains credential-free release binaries and SHA-256 checksums for the LetLeeIn endpoint agent. The private source, build configuration, security design, and deployment infrastructure remain in `Joleeconsultants/LetLeeIn`.

## Current pilot release

`agent-v0.1.0` has a published checksum but predates enforced Authenticode signing. Its EXE is not digitally signed and must not be represented as a signed production release.

Future releases are published only by the private repository's GitHub Action. That workflow builds the EXE and MSI, Authenticode-signs and verifies both files, generates checksums after signing, and then publishes only those approved artifacts here.

Release assets never contain customer identifiers, device credentials, enrollment codes, logs, command results, or private source code. Client enrollment is generated separately through the Cloudflare Access-protected LetLeeIn portal.
