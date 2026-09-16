


# Enterprise Business Vault
#Keeps files in both cold storage and the cloud.
##with offline self-healing geometric file refresh.

**Enterprise Business Vault** is a secure, client-side enterprise document vault and cryptographic asset manager packaged entirely within a single, self-contained HTML file. It provides zero-trust local encryption, robust file integrity verification, automated freshness scrubbing cycles, and direct file system integration using modern browser APIs.

---

## 🔑 Key Features

1. **Zero-Trust Client-Side Encryption**
   - Built on the browser's native **Web Crypto API**.
   - Uses **AES-256-GCM** for authenticated encryption.
   - Key derivation via **PBKDF2** (250,000 iterations with SHA-256). Passphrases are never stored or transmitted; only a salted verifier hash is kept locally to authenticate future sessions.

2. **Custom `.bizvault` File Format**
   - Proprietary binary packaging containing magic bytes (`BIZV`), cryptographic initialization vectors (IV), and authenticated ciphertexts.
   - Preserves original filenames, file sizes, and **CRC32** checksums to prevent silent data corruption.

3. **Freshness & Integrity Verification Cycle**
   - Periodic or manual background scans that decrypt assets, recompute CRC32 plaintext checksums, verify authentication tags, and re-encrypt files with fresh IVs (cold-storing). Self-healing properties of the CRC32 structure cleans up data and repairs it without 3rd party offline scrutiny or cloud based apps.
   - Configurable freshness thresholds and background scan intervals.

4. **Enterprise Business Suite**
   - Store and manage business entity details (Legal Name, Taxpayer ID, Format Labels, Notes) persisted securely in browser local storage.

5. **Advanced Storage & Remote Endpoints**
   - Integrates with the File System Access API (`showDirectoryPicker`) for direct directory read/write access.
   - Built-in remote endpoint testing tool for dispatching HTTP PUT/POST payloads to custom servers, webhooks, or S3 pre-signed URLs.

6. **Self-Hosting Code Inspector & Editor**
   - Built-in source code inspector allowing operators to inspect, edit, download, or launch updated versions of the application as a new live tab directly from the UI.

---

## 🛠️ Technology Stack

- **HTML5 & CSS3**: Responsive, single-file container with built-in dark/light design system variables and custom animations.
- **Vanilla JavaScript (ES6 Modules)**: No external build steps, bundlers, or heavy npm dependencies required.
- **Web Crypto API**: High-performance, hardware-backed cryptographic primitives (`crypto.subtle`).

---

## 🚀 Getting Started

### Prerequisites
Because the application uses the browser's **Web Crypto API**, it requires a secure context (HTTPS or `localhost`). Opening the file via `file://` protocols in some browsers may restrict cryptographic features.

### Quick Start
1. Save the application code as an HTML file (e.g., `vault.html`).
2. Open the file in a modern Chromium-based browser (Chrome, Edge, Brave, etc.).
3. **Sign In**: 
   - On your first visit, enter an **Operator Name** and a secure **Passphrase** to initialize your local account.
   - *Note: If you forget your passphrase, encrypted files cannot be recovered as there is no backend backdoor.*
4. **Choose Storage**: Click **📁 Choose Storage Location** to select a local directory where `.bizvault` files will be saved.
5. **Load & Encode**: Navigate to the **File System & Vault** tab to load plain files, preview them, and encode them into secure `.bizvault` assets.

---

## 🔒 File Format Specification (`.bizvault`)

The `.bizvault` binary structure is assembled as follows:


####WARNING!  First time in this browser: entering a name and passphrase here creates your operator account. The passphrase itself is never stored anywhere — only a salted verification hash, plus it's used live (never saved) to derive your real AES-256-GCM encryption key for this session. If you forget it, any files you encrypted cannot be recovered — there is no backdoor. Please write down your passphrase.  

##NEVER SHARE OR STORE PASSPHRASE WITHOUT COMPLETE TRUST!

Enterprise Buisness Vault Copyright 2026 Joseph La Follette --ALL RIGHTS RESERVED  

Contact 21cetjoe@gmail.com for corporate licensing rates.

