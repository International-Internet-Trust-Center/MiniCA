# MiniCA - Professional Certificate Authority System

MiniCA is a comprehensive PKI (Public Key Infrastructure) system with a modern GUI for managing certificates. It supports full certificate lifecycle management including generation, validation, revocation, and export in multiple formats.

**License**: Proprietary Software License - Public Use Allowed  
**Copyright**: © 2024 Gorq AI Platforms & IITCENTER.EU.ORG  
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
- **PEM**: Base64 encoded certificates and keys
- **DER**: Binary certificate format
- **PKCS#12**: Password-protected certificate bundles
- **PKCS#7**: Certificate chain format
- **JKS**: Java KeyStore format (requires keytool)

### Additional Features
- **Certificate Templates**: Pre-configured certificate types with 14 built-in templates
- **Automated Renewal**: Scheduled certificate renewal with configurable policies
- **Multi-Tenant Support**: Support for multiple organizations with role-based access
- **HSM Integration**: Hardware Security Module support (PKCS#11, Azure Key Vault, AWS KMS)
- **Audit Logging**: Comprehensive audit trail for all operations
- **Database Storage**: SQLite database for persistent data storage
- **Branding Support**: Customizable branding and themes
- Certificate validation and chain verification
- Certificate Revocation List (CRL) generation
- Certificate export in multiple formats
- GUI-based certificate management
- Command-line interface for automation
- Executable and installer creation

## Installation

### Prerequisites
- Python 3.8 or higher
- OpenSSL (must be available in PATH)
- Windows 10/11 (for executable version)

### From Source
1. Clone the repository:
   ```bash
   git clone https://github.com/minica/minica.git
   cd minica
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the application:
   ```bash
   python -m minica.main
   ```

### Using Executable
1. Download the latest release from the releases page
2. Run `MiniCA_Setup.exe` to install
3. Launch MiniCA from the Start menu or desktop shortcut

## Usage

### GUI Mode

#### Initializing PKI
1. Launch MiniCA
2. Click "Initialize PKI" to create the certificate authority hierarchy
3. Wait for the initialization to complete

#### Generating Certificates
1. Click "New Certificate" or go to Certificate → Generate New Certificate
2. Select the certificate type
3. Fill in the subject information
4. Configure additional options (validity period, key size, etc.)
5. Click "Generate"

#### Managing Certificates
- **View Certificates**: Browse all certificates in the "Certificates" tab
- **Export Certificates**: Right-click a certificate and select "Export"
- **Revoke Certificates**: Select a certificate and click "Revoke"
- **Validate Certificates**: Select a certificate and click "Validate"

#### CA Management
- **View CA Information**: Go to CA → CA Information
- **Export CA Bundle**: Export CA certificates and private keys
- **Generate CRL**: Create Certificate Revocation Lists

#### New Features in GUI

**Certificate Templates**
- Access via `Templates` menu
- 14 pre-configured certificate types (SSL Server/Client, Email Signing/S/MIME, Code Signing, Document Signing, Wildcard SSL, Multi-Domain SSL, EV SSL, Client Auth, OCSP Signing, Timestamping)
- Create, edit, duplicate, and manage custom templates
- Import/export template configurations
- Template validation and field requirements

**Renewal Management**
- Access via `Renewal` menu
- Configure renewal policies with triggers (days before expiry, percentage remaining, scheduled dates)
- Actions: Auto-renew, notify-only, escalate, revoke
- Schedule daily, weekly, monthly checks
- Monitor renewal jobs and notifications
- Comprehensive statistics and reporting

**Multi-Tenant Management**
- Access via `Tenants` menu
- Create and manage multiple organizations
- Role-based access control with permissions
- Tenant-specific quotas and limits
- Feature flags per tenant
- Custom branding and domain restrictions
- Data isolation and security

**HSM Configuration**
- Access via `HSM` menu
- Support for PKCS#11, Azure Key Vault, AWS KMS, Google Cloud KMS, HashiCorp Vault
- Manage HSM keys and operations
- Sign, verify, encrypt, decrypt using HSM keys
- Connection testing and monitoring
- Operation logging and statistics

**Audit and Security**
- Access via `Audit` menu
- Comprehensive audit trail for all operations
- Security reports and compliance tracking
- Export audit data for analysis
- User activity monitoring
- System event logging

### Command Line Mode

#### Initialize PKI
```bash
python -m minica.main --init-pki
```

#### List Certificates
```bash
python -m minica.main --list-certs
```

#### Export CA Bundle
```bash
python -m minica.main --export-ca /path/to/output/directory
```

#### Validate Certificate
```bash
python -m minica.main --validate-cert /path/to/certificate.crt
```

## Configuration

### OpenSSL Configuration
MiniCA uses OpenSSL configuration files located in `minica/configs/`:
- `root_ca.cnf`: Root CA configuration
- `intermediate_ca.cnf`: Intermediate CA configuration
- `sub_ca.cnf`: Sub CA configuration
- `ssl_server.cnf`: SSL server certificate configuration
- `ssl_client.cnf`: SSL client certificate configuration
- `email_signing.cnf`: Email signing certificate configuration
- `email_smime.cnf`: S/MIME certificate configuration
- `code_signing.cnf`: Code signing certificate configuration
- `digital_signature.cnf`: Digital signature certificate configuration
- `dsc_encryption.cnf`: DSC + Encryption certificate configuration
- `email_dsc_combo.cnf`: Email + DSC combo certificate configuration

### Certificate Directory Structure
```
certs/
├── root_ca/
│   ├── minica_root_ca.crt
│   ├── minica_root_ca.key
│   ├── minica_root_ca.crl
│   ├── issued_certificates.json
│   └── revoked_certificates.json
├── intermediate_ca/
│   ├── minica_intermediate_ca.crt
│   ├── minica_intermediate_ca.key
│   ├── minica_intermediate_ca.crl
│   ├── issued_certificates.json
│   └── revoked_certificates.json
├── sub_ca/
│   ├── minica_sub_ca.crt
│   ├── minica_sub_ca.key
│   ├── minica_sub_ca.crl
│   ├── issued_certificates.json
│   └── revoked_certificates.json
└── minica_config.json
```

## API Reference

### CertificateManager
Main class for managing certificates and CAs.

```python
from minica.pki.certificate_manager import CertificateManager

# Initialize certificate manager
cert_manager = CertificateManager("certs")

# Initialize PKI hierarchy
cert_manager.initialize_pki_hierarchy()

# Generate SSL server certificate
cert = cert_manager.generate_ssl_server_certificate(
    common_name="example.com",
    alt_names=["www.example.com", "api.example.com"]
)

# Export certificate
exported_files = cert_manager.export_certificate(cert, "exports")
```

### Certificate Types
```python
from minica.pki.certificate import CertificateType

# Available certificate types
CertificateType.ROOT_CA
CertificateType.INTERMEDIATE_CA
CertificateType.SUB_CA
CertificateType.SSL_SERVER
CertificateType.SSL_CLIENT
CertificateType.EMAIL_SIGNING
CertificateType.EMAIL_SMIME
CertificateType.CODE_SIGNING
CertificateType.DIGITAL_SIGNATURE
CertificateType.DSC_ENCRYPTION
CertificateType.EMAIL_DSC_COMBO
```

### Certificate Validation
```python
from minica.pki.validation import CertificateValidator

# Create validator
validator = CertificateValidator()

# Validate certificate
result = validator.validate_certificate(
    cert_file="certificate.crt",
    ca_cert_file="ca.crt",
    check_revocation=True,
    check_expiry=True
)

print(f"Valid: {result['valid']}")
print(f"Errors: {result['errors']}")
print(f"Warnings: {result['warnings']}")
```

## Building from Source

### Prerequisites
- Python 3.8+
- PyInstaller
- NSIS (for installer)

### Build Executable
```bash
python build.py
```

### Build Installer
```bash
makensis installer.nsi
```

## Security Considerations

1. **Private Key Security**: Private keys are stored unencrypted by default. Consider implementing encryption for production use.

2. **Certificate Storage**: Certificates are stored in plain text files. Implement proper access controls.

3. **CRL Distribution**: CRLs are generated locally. Implement proper CRL distribution for production use.

4. **OpenSSL Security**: Ensure OpenSSL is kept up to date with security patches.

5. **Network Security**: If deploying CRL distribution points, use HTTPS and implement proper authentication.

## Troubleshooting

### Common Issues

#### OpenSSL Not Found
**Error**: "OpenSSL is required but not found in PATH"
**Solution**: Install OpenSSL and ensure it's available in your system PATH.

#### Certificate Generation Fails
**Error**: "Failed to generate certificate"
**Solution**: Check that the PKI hierarchy is initialized and OpenSSL is working correctly.

#### GUI Not Starting
**Error**: "Application error"
**Solution**: Ensure all dependencies are installed: `pip install -r requirements.txt`

#### Export Fails
**Error**: "Failed to export certificate"
**Solution**: Check that the certificate files exist and you have write permissions to the output directory.

#### PKI Setup Dialog Error
**Error**: "_tkinter.TclError: cannot use geometry manager grid inside ... which already has slaves managed by pack"
**Solution**: Fixed in latest version. If you encounter this error, ensure you're using the latest code.

#### Feature Manager Initialization Fails
**Error**: "Feature managers initialization failed"
**Solution**: Check that all required dependencies are installed and the database is accessible. The application will continue to run with basic functionality.

### Logs and Debugging
- Check the console output for detailed error messages
- Verify OpenSSL installation: `openssl version`
- Test certificate generation manually using OpenSSL commands

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This software is distributed under a **Proprietary Software License** that allows public use while maintaining closed-source protection. See [LICENSE.txt](LICENSE.txt) for complete terms and conditions.

### Key Points:
- **Public Use Allowed**: Free use for personal, educational, and commercial purposes
- **Closed Source**: Source code and algorithms remain proprietary
- **No Redistribution**: Cannot redistribute, modify, or create derivative works
- **No Reverse Engineering**: Decompiling or reverse engineering is prohibited

For licensing questions or commercial licensing options, contact:
- **Gorq AI Platforms**: https://gorqai.digital
- **IITCENTER.EU.ORG**: https://iitcenter.eu.org

## Support

For support and questions:
- Create an issue on GitHub
- Check the documentation
- Review the troubleshooting section

## Architecture

### Core Components

**PKI Management**
- `minica/pki/`: Certificate Authority and certificate management
- `minica/pki/ca.py`: Base CA classes and implementations
- `minica/pki/certificate_manager.py`: Main certificate operations

**GUI System**
- `minica/gui/`: Tkinter-based user interface
- `minica/gui/main_window.py`: Main application window
- `minica/gui/*_dialog.py`: Feature-specific dialogs

**Database Layer**
- `minica/database/`: SQLite database management
- `minica/database/models.py`: Database models and schemas
- `minica/database/database_manager.py`: Database operations

**New Feature Modules**

**Certificate Templates**
- `minica/templates/`: Template management system
- `minica/templates/certificate_templates.py`: Template manager and operations
- `minica/templates/template_types.py`: Pre-configured template definitions

**Automated Renewal**
- `minica/renewal/`: Certificate renewal system
- `minica/renewal/renewal_manager.py`: Renewal operations and job management
- `minica/renewal/renewal_policy.py`: Policy definitions and triggers
- `minica/renewal/renewal_scheduler.py`: Scheduling and automation

**Multi-Tenant Support**
- `minica/tenant/`: Tenant management system
- `minica/tenant/tenant_manager.py`: Tenant operations and isolation
- `minica/tenant/tenant_models.py`: Tenant, user, and policy models

**HSM Integration**
- `minica/hsm/`: Hardware Security Module support
- `minica/hsm/hsm_manager.py`: HSM operations and key management
- `minica/hsm/hsm_providers.py`: Provider implementations (PKCS#11, Azure, AWS)
- `minica/hsm/hsm_models.py`: HSM configuration and key models

**Audit and Security**
- `minica/audit/`: Audit logging system
- `minica/audit/audit_manager.py`: High-level audit operations
- `minica/audit/audit_logger.py`: Low-level logging implementation

**Branding and Theming**
- `minica/branding/`: Application branding system
- `minica/branding/brand_manager.py`: Brand management and theming
- `minica/branding/colors.py`: Color palettes and themes
- `minica/branding/fonts.py`: Font definitions and styles

### Data Flow

1. **User Interaction**: GUI captures user input and actions
2. **Business Logic**: Feature managers process requests and validate data
3. **Database Operations**: Data is persisted using SQLAlchemy models
4. **Audit Logging**: All operations are logged for security and compliance
5. **External Integration**: HSM providers handle hardware security operations

### Security Features

- **Role-Based Access Control**: Granular permissions per user and tenant
- **Audit Trail**: Comprehensive logging of all system operations
- **HSM Support**: Hardware-backed key operations for enhanced security
- **Data Isolation**: Tenant-specific data separation and access controls
- **Encryption**: Secure storage of sensitive configuration data

## Changelog

### Version 2.0.0
- **Certificate Templates**: 14 pre-configured certificate types with custom template support
- **Automated Renewal**: Scheduled certificate renewal with configurable policies
- **Multi-Tenant Support**: Multiple organizations with role-based access control
- **HSM Integration**: Hardware Security Module support (PKCS#11, Azure Key Vault, AWS KMS)
- **Audit Logging**: Comprehensive audit trail and security reporting
- **Database Storage**: SQLite database for persistent data storage
- **Branding Support**: Customizable branding and themes
- **Enhanced GUI**: New dialogs and menu system for all features
- **Improved Security**: Enhanced security features and compliance tracking

### Version 1.0.0
- Initial release
- Full PKI hierarchy support
- GUI and CLI interfaces
- Multiple certificate types
- Export functionality
- Certificate validation
- CRL generation
- Executable and installer support

## Roadmap

- [x] Certificate templates
- [x] Automated certificate renewal
- [x] Hardware security module (HSM) support
- [x] Multi-tenant support
- [x] Audit logging and security reporting
- [ ] OCSP responder
- [ ] Certificate transparency logs
- [ ] REST API
- [ ] Web interface
- [ ] Certificate monitoring and alerts
- [ ] Integration with Active Directory
- [ ] Multi-platform support (Linux, macOS)
