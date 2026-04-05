# BraveDebloat – Debloat MacOS profile for Brave.

A `.mobileconfig` profile for macOS that disables Brave Browser's crypto, AI, VPN, and telemetry features using managed policy keys. Settings are locked at the system level and apply immediately after installation.

## What it does

**Brave-specific**

- Disables Brave Rewards (BAT)
- Disables Brave Wallet
- Disables Brave VPN
- Disables Leo AI
- Disables Tor private windows
- Disables Brave Talk
- Disables Brave News
- Disables Playlist
- Disables Speedreader
- Disables P3A analytics, stats ping, and Web Discovery

**Chromium-level hardening**
- Sets geolocation to ask-before-sharing
- Disables feedback surveys

## Installation

1. Download `BraveDebloat.mobileconfig`
2. Double-click the file — System Settings will open automatically
3. Go to **System Settings → Privacy & Security → Profiles** and approve the profile
4. Relaunch Brave
5. Verify by navigating to `brave://policy` — all applied keys will be listed there

## Notes

**Bundle ID:** The profile targets `com.brave.Browser` (stable channel). If you use a different channel, edit the bundle ID in the file:

- Beta: `com.brave.Browser.beta`
- Nightly: `com.brave.Browser.nightly`

**UUIDs:** The file ships with placeholder UUIDs. For personal use this is fine. If you are deploying via MDM, replace both UUIDs with fresh values by running `uuidgen` in Terminal.

**Default browser:** macOS does not allow profiles to set the default browser. Change it manually at **System Settings → Desktop & Dock → Default web browser**.

**Removing the profile:** Go to **System Settings → Privacy & Security → Profiles**, select the profile, and click the minus button. Brave will return to its defaults on next launch.

## Verification

After installation, open `brave://policy` in Brave. Policies with a green status are active. If any show an error, the key name or value type may be mismatched for your version of Brave.

## Compatibility

Tested on macOS Sonoma and Sequoia with Brave stable. Most Chromium-inherited policy keys require Brave 1.3 or later. Brave-specific keys (prefixed `Brave*`) were introduced at various versions — check `brave://policy` for any that show as unrecognised.

## References

- [Brave Group Policy documentation](https://support.brave.app/hc/en-us/articles/360039248271-Group-Policy)
- [Chrome Enterprise policy list](https://chromeenterprise.google/policies/) (most keys apply to Brave)
- [brave-core policy definitions](https://github.com/brave/brave-core/tree/master/components/policy/resources/templates/policy_definitions/BraveSoftware)
