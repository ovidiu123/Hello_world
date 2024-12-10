# PKI Automation Script

## Author:
**Lupan Ovidiu**  
FAF-223

---

## Overview
This project automates the process of setting up a Public Key Infrastructure (PKI) using Python and OpenSSL. It includes the generation of a root Certificate Authority (CA), user certificates, signing and verifying files, and revoking certificates. The script is designed to simplify the creation of a secure certificate-based system.

---

## Components:
The following components are implemented in the PKI script:

1. **Root CA**: A self-signed certificate authority used to issue other certificates.
2. **User Certificate**: A certificate issued by the Root CA to identify the user.
3. **Private Keys**: Secure keys used for signing and verifying certificates and files.
4. **CRL (Certificate Revocation List)**: A list of revoked certificates.
5. **Signed Files**: Files that are signed using a private key to verify authenticity.

---

## Features:
- **Automated Certificate Generation**: Generates root and user certificates without requiring manual intervention.
- **File Signing & Verification**: Signs files with private keys and verifies them with corresponding public keys.
- **Certificate Revocation**: Supports revocation of certificates and updating the Certificate Revocation List (CRL).
- **OpenSSL Integration**: Uses OpenSSL commands to perform cryptographic operations like key generation, signing, and verification.

---

## Usage:
### Running the Script:
To run the script, use the following command:

```bash
python mainlab5.py
