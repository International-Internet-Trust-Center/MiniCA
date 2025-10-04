# MiniCA Professional Certificate Authority System

**Version**: 1.0.0  
**Release Date**: 2025-10-04  
**Developed by**: Gorq AI Platforms & IITCENTER.EU.ORG  
**Published by**: International Internet Trust Center

## 🎉 About MiniCA

MiniCA is a comprehensive PKI (Public Key Infrastructure) system with a modern GUI for managing certificates. It supports full certificate lifecycle management including generation, validation, revocation, and export in multiple formats.

## 📦 Download Options

### Windows
- **MiniCA-Professional-Installer.exe** - Professional NSIS installer (Recommended)
- **MiniCA-Simple-Installer.zip** - Simple batch installer
- **MiniCA-GUI-Installer.zip** - Python-based GUI installer

### Linux (Ubuntu/Debian)
- **install.sh** - Linux installation script
- **uninstall.sh** - Linux uninstallation script
- **README.md** - Linux-specific documentation

## ✨ Features

- **Full PKI Hierarchy Management**: Root CA, Intermediate CA, Sub CA
- **Certificate Generation**: SSL, DSC, S/MIME, Code Signing certificates
- **Certificate Templates**: Pre-configured certificate types
- **Automated Renewal**: Scheduled certificate renewal
- **Multi-Tenant Support**: Support for multiple organizations
- **HSM Integration**: Hardware security module support
- **Backup and Restore**: Comprehensive data backup and restore
- **Audit Logging**: Security and compliance reporting
- **Advanced Certificate Attributes**: Manual EKU and attribute selection
- **Professional Branding**: Modern UI with splash screen

## 🖥️ System Requirements

### Windows
- Windows 10/11 (64-bit recommended)
- Administrator privileges for installation
- 50 MB free disk space

### Linux
- Ubuntu 18.04+ or Debian 10+
- Python 3.8+
- Tkinter (python3-tk)
- 50 MB free disk space

## 🚀 Quick Start

### Windows Installation
1. Download `MiniCA-Professional-Installer.exe`
2. Right-click → "Run as administrator"
3. Follow the installation wizard
4. Launch MiniCA from Desktop or Start Menu

### Linux Installation
```bash
# Download and run installer
wget https://github.com/iitcenter/minica/releases/latest/download/install.sh
chmod +x install.sh
./install.sh
```

## 📋 Installation Guide

### Windows
1. **Choose Installer**: Select the appropriate installer for your needs
2. **Run as Administrator**: Right-click installer → "Run as administrator"
3. **Follow Wizard**: Complete the installation wizard
4. **Configure**: Initialize PKI hierarchy on first run

### Linux
1. **Download**: Get the Linux installer script
2. **Make Executable**: `chmod +x install.sh`
3. **Run**: `./install.sh`
4. **Configure**: Initialize PKI hierarchy on first run

## ⚠️ Important Notes

### Windows Defender
- Windows Defender may flag the executable as potentially unwanted software
- See `WINDOWS_DEFENDER_GUIDE.md` for exclusion instructions
- Add MiniCA.exe to Windows Defender exclusions

### Linux Dependencies
- Ensure Python 3.8+ is installed
- Install Tkinter: `sudo apt install python3-tk`
- Run installer with appropriate permissions

## 📚 Documentation

- **README.md** - Main documentation
- **LICENSE.txt** - License terms and conditions
- **LICENSE_SUMMARY.md** - License summary
- **WINDOWS_DEFENDER_GUIDE.md** - Windows security configuration
- **INSTALLER_SUMMARY.md** - Installer details

## 🔧 Development

### Source Code
- Source code is proprietary and not included in this release
- Contact developers for source code licensing options
- Pre-built executables and installers are provided

## 🤝 Support

### Contact Information
- **Gorq AI Platforms**: https://gorqai.digital
- **IITCENTER.EU.ORG**: https://iitcenter.eu.org
- **International Internet Trust Center**: https://iitcenter.eu.org

### Getting Help
1. Check the documentation in `documentation/` folder
2. Review Windows Defender guide for security issues
3. Contact support through project channels

## 📄 License

**Proprietary Software License - Public Use Allowed**

This software is distributed under a proprietary license that allows public use while maintaining closed-source protection. See `LICENSE.txt` for complete terms and conditions.

### Key Points:
- ✅ **Public Use Allowed**: Free use for personal, educational, and commercial purposes
- ❌ **Closed Source**: Source code and algorithms remain proprietary
- ❌ **No Redistribution**: Cannot redistribute, modify, or create derivative works
- ❌ **No Reverse Engineering**: Decompiling or reverse engineering is prohibited

## 🏢 About the Developers

### Gorq AI Platforms
- **Website**: https://gorqai.digital
- **Focus**: AI-powered solutions and platforms

### International Internet Trust Centre (IITCENTER.EU.ORG)
- **Website**: https://iitcenter.eu.org
- **Focus**: Internet trust, security, and certificate authority services

## 🔄 Version History

### v1.0.0 (Current)
- Initial release
- Full PKI hierarchy management
- Certificate generation and management
- Advanced features (templates, renewal, multi-tenant, HSM)
- Backup and restore functionality
- Audit logging and security reporting
- Professional branding and UI

## 📊 System Architecture

- **Frontend**: Tkinter-based GUI
- **Backend**: Python with OpenSSL integration
- **Database**: SQLite for data persistence
- **Security**: Comprehensive audit logging
- **Multi-Platform**: Windows and Linux support

---

**MiniCA Professional Certificate Authority System**  
Copyright © 2024 Gorq AI Platforms & IITCENTER.EU.ORG  
All Rights Reserved  

Published by International Internet Trust Center  
https://iitcenter.eu.org
