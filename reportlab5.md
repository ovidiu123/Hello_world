# PKI Script Report

## Author:
**Lupan Ovidiu**  
FAF-223

---

## Project Overview:
This project implements a Public Key Infrastructure (PKI) system using OpenSSL. It covers the steps of generating root and user certificates, signing and verifying files, and handling certificate revocation. The PKI structure is created and managed through Python scripts.

---

## Table of Contents:
- [Introduction](#introduction)
- [PKI Setup](#pki-setup)
- [Key Features](#key-features)
- [Usage](#usage)
- [Installation](#installation)
- [Commands Overview](#commands-overview)
- [Script Workflow](#script-workflow)
- [Conclusion](#conclusion)

---

## Introduction:
This Python-based PKI script automates the creation of a Certificate Authority (CA), user certificates, file signing, and certificate revocation using OpenSSL. The script performs the following operations:
- Set up a CA directory structure.
- Generate a Root CA certificate and private key.
- Generate user keys, Certificate Signing Requests (CSR), and certificates.
- Sign files with user keys and verify signatures.
- Revoke user certificates and generate a Certificate Revocation List (CRL).

---

## PKI Setup:
The script sets up the following directory structure for the PKI system:


### Main Components:
- **Root CA Certificate**: A self-signed certificate used to sign other certificates.
- **User Certificate**: A certificate issued by the Root CA for the user.
- **Private Keys**: Secure keys for the Root CA and User to sign and verify certificates.
- **Certificate Revocation List (CRL)**: A list of revoked certificates.

---

## Key Features:
- **Automated Setup**: The script sets up directories, generates private keys, CSRs, and certificates automatically.
- **Signing & Verification**: It provides functionality to sign a file with the user’s private key and verify the signature.
- **Certificate Revocation**: It includes functionality to revoke user certificates and generate a CRL.
- **OpenSSL Integration**: Utilizes OpenSSL commands for cryptographic operations.

---

## Usage:
The PKI script performs the following operations:
1. **Set up the CA directory**.
2. **Generate the Root CA's private key and self-signed certificate**.
3. **Generate user private key, CSR, and user certificate**.
4. **Sign a file with the user's private key**.
5. **Verify the signature of a file**.
6. **Revoke the user's certificate and generate a CRL**.

### Running the Script:
To execute the script, run the following command in the terminal:
```bash
python mainlab5.py
