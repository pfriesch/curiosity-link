# Curiosity Link

Curiosity Link is a Windows tool designed to facilitate secure access to local files, folders, and network locations from within cloud or on-premises [Curiosity Workspaces](https://curiosity.ai/workspace) through specially crafted links. It supports two URI schemes: `curiosity-open://` for opening files and `curiosity-show://` for revealing files or folders in File Explorer.

## Features

- **Secure Links**: Utilizes SHA3-512 Public/Private RSA key pairs to sign and verify links, ensuring the integrity and authenticity of accessed resources.
- **Key Management**: Provides commands to generate the required public/private key files automatically.
- **Signature Verification**: Verifies that accessed resources are authorized using SHA3-512 hashing and RSA signature padding.

## Installation

1. Download the latest release from the [Releases](https://github.com/curiosity-ai/curiosity-link/releases) page.
2. Run the command `Curiosity-Link create-key-pair` to create the required Public/Private key files.
3. Place the executable and the `curiosity-link.public-key.pem` in a directory included in your user's devices, and schedule the 'Curiosity-Link.exe' to run once after login for your users, using for example a GPO Logon Script (this will register the URI schemas appropriately).
4. Upload the `curiosity-link.private-key.pem` file to your Curiosity Workspace.
5. Use the Curiosity CLI to sync your local and network folders to the Curiosity Workspace. 
