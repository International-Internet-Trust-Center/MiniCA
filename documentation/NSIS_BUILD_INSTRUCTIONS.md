# Manual NSIS Installer Build Instructions

## Option 1: Install NSIS and Build

1. **Download NSIS**:
   - Go to: https://nsis.sourceforge.io/Download
   - Download the latest version (3.09 or newer)
   - Run the installer with default settings

2. **Build the installer**:
   ```cmd
   python build_nsis_installer.py
   ```

## Option 2: Use Portable NSIS

1. **Download NSIS Portable**:
   - Extract NSIS to a folder (e.g., C:\NSIS)
   - Add makensis.exe to your PATH or use full path

2. **Build manually**:
   ```cmd
   makensis MiniCA-Installer.nsi
   ```

## Option 3: Use Online NSIS Builders

1. **NSIS Online Builder**:
   - Upload the .nsi script to an online NSIS compiler
   - Download the compiled installer

## Option 4: Use Alternative Installer Tools

### Inno Setup (Alternative to NSIS)
1. Download Inno Setup from: https://jrsoftware.org/isinfo.php
2. Convert the NSIS script to Inno Setup format
3. Build the installer

### Advanced Installer (Commercial)
1. Download Advanced Installer
2. Import the project files
3. Build the installer

## Current Status

✅ NSIS script created: `MiniCA-Installer.nsi`
✅ Build script created: `build_nsis_installer.py`
✅ All required files prepared
❌ NSIS not installed (manual installation required)

## Files Ready for Installation

- `dist/MiniCA.exe` - Main executable
- `README.md` - Documentation
- `LICENSE.txt` - License file
- `WINDOWS_DEFENDER_GUIDE.md` - Security guide
- `minica/configs/` - Configuration templates
- `examples/` - Example files
- `samples/` - Sample certificates
- `openssl/` - OpenSSL integration

## Next Steps

1. Install NSIS manually
2. Run: `python build_nsis_installer.py`
3. Or use one of the alternative methods above

---
Developed by Gorq AI Platforms & IITCENTER.EU.ORG
