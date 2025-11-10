# Curiosity Link

**Curiosity Link** is a Windows utility that securely registers and handles local file and folder links for Curiosity Workspaces. It ensures that only authorized, signed links can open or reveal local or network resources on a user’s device.

---

## Overview

Curiosity Link provides a secure bridge between Curiosity Workspaces and local file systems. It registers custom URI schemes that allow Workspace links to open or reveal files and folders directly on Windows, after verifying their authenticity using RSA public-key signatures.

It supports two URI schemes:

* `curiosity-open://` — opens a file with its default application
* `curiosity-show://` — reveals a file or folder in File Explorer

---

## Features

* **RSA Signature Verification** — validates every link with SHA3-512 and RSA signature padding before opening it.
* **Workspace Certificate Binding** — ensures links only work when signed for the correct Workspace.
* **Secure Local Access** — prevents tampering or misuse of local file links.
* **Automatic URI Scheme Registration** — registers Curiosity URI handlers on first launch or via CLI.

---

## Installation

1. **Download** the latest release of `Curiosity-Link.exe` from the Releases page.
2. **Place** the workspace’s public key file (`<workspace-name>.curiosity-link.public-key.pem`) in the same directory as `Curiosity-Link.exe`.
3. **Register URI schemes** on user devices:

   ```bash
   Curiosity-Link register
   ```

   This can also be done interactively by running `Curiosity-Link.exe` without parameters.
4. **Deploy** both files (the executable and public key) to user machines, for example using a logon script or GPO.

---

## Usage

Curiosity Link automatically processes `curiosity-open://` and `curiosity-show://` links once registered.

When a user clicks such a link:

1. The app decodes the path.
2. Verifies the RSA signature using the provided public key.
3. Confirms that the key matches the Workspace.
4. Opens or reveals the target file/folder if valid.

If validation fails, an error message is shown instead.

---

## Command Reference

| Command                   | Description                                                |
| ------------------------- | ---------------------------------------------------------- |
| `Curiosity-Link`          | Runs interactively, registering URI schemes if none exist. |
| `Curiosity-Link register` | Registers URI schemes silently (for automation).           |

---

## Security

* Verifies all links using **RSA public-key cryptography** with **SHA3-512** hashing.
* Rejects unsigned, tampered, or mismatched links.
* Only accepts links for the Workspace that matches the loaded certificate.
