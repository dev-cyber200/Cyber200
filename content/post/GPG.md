+++
author = "dev@cyber200"
title = "GPG Key"
date = "2024-06-30"
description = "GNU Privacy Guard (GPG) is an encryption tool that provides cryptographic privacy and authentication. It is often used to secure communication by encrypting and signing data and communications. GPG is an implementation of the OpenPGP standard as defined by RFC 4880."
tags = [
    "gpg",
    "dev-kit",
]
+++

## Key Concepts

1. Public and Private Keys: GPG uses a pair of keys – a public key and a private key.

- Public Key: This key is shared openly and used to encrypt data.
- Private Key: This key is kept secret and used to decrypt data encrypted with the corresponding public key.
2. Encryption: The process of converting plaintext into ciphertext using a key.

3. Decryption: The process of converting ciphertext back into plaintext using a key.

4. Digital Signatures: A cryptographic signature that verifies the sender's identity and ensures that the data has not been tampered with.

## How GPG Works
1. Generating Keys
To use GPG, you first need to generate a pair of keys. This can be done using the following command:
```bash
gpg --gen-key
```

2. Distributing the Public Key
Once the keys are generated, you can distribute your public key to others so they can send you encrypted messages. Export your public key with:

```bash
gpg --export -a "Your name" \
> plublic_key.asc
```

You can then share public_key.asc with anyone who wants to send you encrypted messages.

3. Importing Public Keys
To encrypt a message to someone else, you need their public key. You can import their public key into your GPG keyring:
```bash
gpg --import public_key.asc
```

4. Encrypting Messages
To send an encrypted message, you use the recipient’s public key:
```bash
gpg --encrypt --recipient \
recipient@ss.com message.txt
```

This command will create an encrypted version of message.txt, typically with a .gpg extension.

5. Decrypting Messages
```bash
gpg --decrypt message.txt.gpg
```

You will be prompted to enter the passphrase for your private key.

6. Signing Messages
To sign a message or file, you use your private key to create a digital signature:
```bash
gpg --sign message.txt
```

This command will create a signed version of message.txt (e.g., message.txt.gpg) that includes the digital signature.

7. Verifying Signatures
When you receive a signed message, you can verify the signature using the sender’s public key:
```bash
gpg --verify message.txt.gpg
```

This command will check the signature and confirm whether the message was signed by the corresponding private key and whether the message has been altered.

Combining Encryption and Signing
```bash
gpg --encrypt --sign --recipient\
recipient@ss.com message.txt
```
