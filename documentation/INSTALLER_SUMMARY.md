# MiniCA Professional Installer Summary

## Installer Files Created

### 1. NSIS Professional Installer (Recommended)
- **File**: `MiniCA-Professional-Installer.exe`
- **Type**: Full-featured Windows installer
- **Features**:
  - Modern UI with welcome screens
  - Component selection (Core, Shortcuts, OpenSSL, Samples)
  - Custom installation directory
  - Desktop and Start Menu shortcuts
  - Uninstaller with registry cleanup
  - Add/Remove Programs integration
  - License agreement
  - Progress tracking

### 2. Simple Batch Installer
- **File**: `MiniCA-Simple-Installer.zip`
- **Type**: Batch script installer
- **Features**:
  - Simple batch file installation
  - No dependencies
  - Quick setup

### 3. GUI Python Installer
- **File**: `MiniCA-GUI-Installer.zip`
- **Type**: Python-based GUI installer
- **Features**:
  - Tkinter-based interface
  - Progress bar
  - Custom options

## Installation Options

### Option 1: NSIS Installer (Recommended)
1. Download `MiniCA-Professional-Installer.exe`
2. Right-click → "Run as administrator"
3. Follow the installation wizard
4. Choose components to install
5. Complete installation

### Option 2: Simple Installer
1. Extract `MiniCA-Simple-Installer.zip`
2. Run `install.bat` as administrator
3. Follow prompts

### Option 3: GUI Installer
1. Extract `MiniCA-GUI-Installer.zip`
2. Run `install.bat` or `install.py`
3. Use graphical interface

## What Gets Installed

### Core Components
- `MiniCA.exe` - Main application (18.0 MB)
- Configuration templates
- Documentation files
- Uninstaller

### Optional Components
- Desktop shortcut
- Start Menu shortcuts and program group
- OpenSSL binaries (if selected)
- Sample certificates and configurations
- Example files

## System Requirements

- Windows 10/11 (64-bit recommended)
- Administrator privileges for installation
- 50 MB free disk space
- Internet connection (for updates)

## Post-Installation

1. **Windows Defender**: Add MiniCA.exe to exclusions
2. **First Run**: Initialize PKI hierarchy
3. **Documentation**: Read included README files

## Features Included

- Full PKI hierarchy management
- Certificate generation (SSL, DSC, S/MIME, Code Signing)
- Certificate templates and automated renewal
- Multi-tenant support
- HSM integration
- Backup and restore functionality
- Audit logging and security reporting
- Advanced certificate attributes configuration
- Professional branding and splash screen

## Support

- Check `WINDOWS_DEFENDER_GUIDE.md` for security settings
- Read `README.md` for detailed usage
- Refer to `INSTALLER_GUIDE.md` for troubleshooting

---
Developed by Gorq AI Platforms & IITCENTER.EU.ORG
