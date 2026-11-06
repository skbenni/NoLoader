# Release process

Tagged `noloader-v*` releases are built by `.github/workflows/noloader-release.yml`. A Windows x64 release contains the prepared launcher archive, self-contained installer, signed Tauri updater executable and signature, `latest.json`, and signed catalog. The installer reads the catalog from this repository's `noloader-catalog` branch and verifies its signature, archive size, and SHA-256 before installing. The launcher checks this repository's signed release feed; it does not query the NoRisk updater. Existing installations need a one-time migration with NoLoader Setup because they use the previous updater endpoint and key.

Find the current published version and artifacts on the [GitHub Releases page](https://github.com/skbenni/NoLoader/releases/latest). The extension host version embedded in a launcher (currently `0.6.30-noloader.4`) is separate from its product release version.

Before publishing a prepared launcher, a release must identify:

- exact upstream commit and NoLoader commit;
- NoLoader API and launcher versions;
- target operating system and architecture;
- toolchain and reproducible build inputs;
- artifact SHA-256 and a verifiable release signature;
- source changes and GPL-3.0 notices;
- third-party runtime/native dependency licenses.

The installer requires explicit confirmation before replacing the selected launcher folder, retains backups, and can restore the recorded original NoRisk folder after later updates. The release workflow also renews the signed catalog weekly. The Tauri updater key and catalog signing key are separate GitHub Actions secrets; neither private key belongs in the repository or release artifacts.
