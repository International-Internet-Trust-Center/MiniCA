# MiniCA - Professional Certificate Authority System

MiniCA is a comprehensive PKI (Public Key Infrastructure) system with a modern GUI for managing certificates. It supports full certificate lifecycle management including generation, validation, revocation, and export in multiple formats.

**License**: Proprietary Software License - Public Use Allowed  
**Copyright**: © 2025 Gorq AI Platforms & IITCENTER.EU.ORG  
**All Rights Reserved**

## Features

### Certificate Authority Hierarchy
- **Root CA**: Self-signed root certificate authority
- **Intermediate CA**: Intermediate certificate authority signed by root CA
- **Sub CA**: Sub certificate authority signed by intermediate CA

### Certificate Types Supported
- **SSL/TLS Certificates**
  - Server certificates with Subject Alternative Names (SAN)
  - Client certificates for mutual authentication
- **Email Certificates**
  - Email signing certificates
  - S/MIME certificates for email encryption
- **Digital Signature Certificates**
  - Document signing certificates
  - DSC + Encryption combo certificates
  - Email + DSC combo certificates
- **Code Signing Certificates**
  - Software code signing certificates

### Export Formats
- **PEM**: Privacy-Enhanced Mail format
- **DER**: Distinguished Encoding Rules format
- **PKCS#12**: Personal Information Exchange format

### Additional Features
- **Certificate Validation**: Built-in certificate validation and verification
- **CRL Generation**: Certificate Revocation List generation and management
- **Template System**: Pre-configured certificate templates
- **Audit Logging**: Comprehensive audit trail and logging
- **Multi-tenant Support**: Support for multiple organizations
- **HSM Integration**: Hardware Security Module support
- **Backup & Restore**: Data backup and disaster recovery
- **Automatic Updates**: GitHub release integration

## Installation

### Windows
- **MiniCA-Professional-Installer.exe** - Professional installer (Recommended)

### Linux (Ubuntu/Debian)
- **minica_1.0.0_amd64.tar.gz** - Linux package with .deb structure
- **install-minica.sh** - Linux installation script

## System Requirements

### Windows
- Windows 10/11 (64-bit recommended)
- Administrator privileges for installation
- 50 MB free disk space

### Linux
- Ubuntu 18.04+ or Debian 10+
- Python 3.8+
- Tkinter (python3-tk)
- 50 MB free disk space

## Support

- **GitHub**: https://github.com/International-Internet-Trust-Center/MiniCA
- **Issues**: https://github.com/International-Internet-Trust-Center/MiniCA/issues
- **Email**: admin@iitcenter.eu.org

## License

Proprietary Software License - Public Use Allowed  
Copyright © 2025 Gorq AI Platforms & IITCENTER.EU.ORG  
All Rights Reserved