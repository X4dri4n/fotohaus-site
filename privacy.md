---
layout: default
title: Privacy Policy
permalink: /privacy

---

# Privacy Policy
Last updated: October 2026

## The short version

Fotohaus has no servers and stores nothing of yours anywhere. We collect no data about you. Where your photos live is entirely your decision — and the app tells you before it moves anything.

## 1. Data Collection

Fotohaus collects no data. There are no analytics, no tracking pixels, no advertising SDKs, and no telemetry of any kind. Nothing is sent to Fotohaus, because there is no Fotohaus server to send it to.

**During the beta:** builds distributed through TestFlight have crash reporting provided by Apple. If the app crashes on your device, Apple may send a diagnostic report — device model, iOS version, and a technical stack trace — to the developer. It contains no photos and no personal content. This is Apple's mechanism, described in Apple's TestFlight terms, and it stops when the app ships on the App Store.

## 2. Network Access

Fotohaus makes no network connections of its own. It has no backend, no API, and no analytics endpoint.

It does ask iOS to fetch **your own** data on your behalf, in one case:

- **Photos stored in iCloud.** If you use "Optimize iPhone Storage", some of your full-resolution originals live in iCloud rather than on your device. When you move such a photo into the vault, Fotohaus asks the system to download your original first, because it cannot encrypt a file it doesn't have. That is your photo travelling from your iCloud account to your phone. Nothing is sent to us, and nothing goes anywhere else. The app shows you when this is happening and asks you to acknowledge it the first time.

Downloads follow whatever you have already set in Settings → Photos → Cellular Data. Fotohaus does not override that choice.

## 3. Photo Library Access

Fotohaus uses Apple's PhotoKit framework to access your photo library. It does three things with that access, and you initiate all three:

- **Reads** your photos and videos, to display and organize them
- **Deletes** an original from your library, when you move a photo into the vault. iOS always asks you to confirm this, and that confirmation cannot be suppressed by the app
- **Creates** a new photo in your library, when you restore an item from the vault

All of this happens on your device.

**One consequence worth knowing:** if you have iCloud Photos enabled, restoring an item from the vault puts it back into your library, where iCloud will sync it as it would any other photo. Moving something into the vault takes it out of that sync; restoring it puts it back in.

**What the app records about your library.** Albums you create in Fotohaus are kept in the app's own database, not in your photo library. For each one it stores the name you gave it, its position in the list, and — for every photo in it — the identifier iOS assigns that photo. These records are not encrypted. They describe photos that are sitting unencrypted in your photo library anyway, so encrypting them would protect nothing; what matters is that they never leave your device, and they don't. Album names are the one piece of text here you wrote yourself, so if you would not want an album called by its name to be readable by someone with your unlocked phone and the right tools, name it something else. Albums *inside* the vault are a separate thing and are encrypted — see section 4.

Earlier versions also cached a place name and coordinates for each geotagged photo so you could search by city. That was removed: looking a place name up meant sending your photo's coordinates to Apple's geocoding service, which contradicted this policy's first sentence. Search by place name is gone with it, and the app deletes any rows an earlier version had written.

## 4. Vault & Encryption

Vault photos and videos are encrypted with AES-256 in GCM mode using Apple's CryptoKit framework, and stored in the app's sandbox. Your PIN is converted into the encryption key on your device using PBKDF2-SHA256 with 600,000 rounds. The PIN itself is never stored — only a verification fingerprint that proves the right PIN was entered. Biometric authentication is handled entirely on-device by the Secure Enclave; biometric data never leaves your device and never reaches Fotohaus.

**What is encrypted.** The photos and videos themselves, their thumbnails, and everything that describes them: when a photo was taken, its dimensions, its location, its EXIF, its original filename, where it came from, whether its library original was deleted, and whether you marked it a favourite. Vault album titles, cover images and member lists are encrypted too.

**What isn't.** The app's local database is not encrypted, though it is stored with iOS file protection and excluded from device backups. For each vault item it records an internal filename, the file size, whether the item is a photo or a video, and the date you added it to the vault. It also records how many albums you have and their order. Someone with access to your unlocked device and the right tools could learn how many items your vault holds, how large they are, which of them are videos, and when each was added. They could not see the items, when or where they were taken, what they were called, or which albums they are in.

**Deleting the app deletes the vault.** Vault contents live only in the app's sandbox and are excluded from iCloud and device backups by design. There is no copy anywhere else. Use Export Vault if you want a backup.

## 5. Planned Connectivity — Not Available in This Version

This section describes where Fotohaus is going, so you know what to expect. **None of it exists yet**, and this section will be rewritten in the present tense on the release that ships it.

A future release is planned to let you back the vault up to **your own** NAS or self-hosted storage. When it ships:

- Fotohaus will connect only to a server address you provide (WebDAV, SMB, or S3-compatible)
- Credentials will be stored in the iOS Keychain
- No data will route through Fotohaus or any third party — your device will talk directly to your server
- It will be opt-in, and the app will remain fully usable without it

The reason this is the direction: the point of Fotohaus is that your data goes where **you** decide. A backup you control on hardware you own is that principle extended, not a departure from it. What will never happen is a Fotohaus-operated server, because there isn't one and there won't be.

## 6. Third-Party Services

Fotohaus integrates no third-party services. There are no advertising networks, no analytics platforms, and no cloud functions. Aside from Apple's own TestFlight crash reporting during the beta (§1), no component of this app reports anything to anyone.

## 7. Data Sharing

There are no servers, no backend, and no data sharing. When you share a photo using iOS's Share Sheet, the destination is determined by the system extension you choose (Messages, Mail, AirDrop, and so on) — Fotohaus does not see, intercept, or log what you share.

## 8. Children's Privacy

Fotohaus collects no personal data from anyone, including children. We do not knowingly collect information from users of any age, because we collect no information at all. The app has no accounts, no messaging, and no user-generated content visible to others.

## 9. Changes to This Policy

As features evolve, this policy will be updated both in-app and at its published web address. The core principle does not change: your data goes only where you tell it to. Material changes will be noted in release notes.

## 10. Contact

Questions or concerns about this policy: support@fotohaus.app
