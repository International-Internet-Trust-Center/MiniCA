# MiniCA Linux Build Instructions

## Overview

This document provides instructions for building actual Linux executables for MiniCA. The packages in this release contain placeholder executables that explain how to build the real packages.

## Prerequisites

### System Requirements
- **Linux distribution**: Ubuntu 18.04+, Debian 10+, or similar
- **Python**: 3.8 or higher
- **Memory**: 2GB RAM minimum, 4GB recommended
- **Disk space**: 1GB free space for build process

### Required Packages
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install python3 python3-pip python3-tk python3-dev build-essential

# Install Python dependencies
pip3 install pyinstaller pyOpenSSL cryptography

# For AppImage creation
wget https://github.com/AppImage/AppImageKit/releases/download/continuous/appimagetool-x86_64.AppImage
chmod +x appimagetool-x86_64.AppImage
sudo mv appimagetool-x86_64.AppImage /usr/local/bin/appimagetool

# For .deb package creation (already installed on Debian/Ubuntu)
# dpkg-deb is usually pre-installed
```

## Building Linux Packages

### Step 1: Prepare Source Code
```bash
# Extract source code
tar -xzf source/minica-source.tar.gz
cd minica-source

# Install Python dependencies
pip3 install -r requirements.txt
```

### Step 2: Build Linux Executable
```bash
# Run the Linux build script
python3 build_linux_proper.py
```

This will create:
- `dist/minica` - Linux executable
- `MiniCA-x86_64.AppImage` - AppImage package
- `minica_1.0.0_amd64.deb` - Debian package
- `minica-linux.tar.gz` - tar.gz package

### Step 3: Test the Build
```bash
# Test the executable
./dist/minica

# Test AppImage
chmod +x MiniCA-x86_64.AppImage
./MiniCA-x86_64.AppImage

# Test .deb package
sudo dpkg -i minica_1.0.0_amd64.deb
minica
```

## Package Details

### AppImage
- **File**: `MiniCA-x86_64.AppImage`
- **Size**: ~18 MB
- **Type**: Portable executable
- **Installation**: None required
- **Usage**: `chmod +x MiniCA-x86_64.AppImage && ./MiniCA-x86_64.AppImage`

### Debian Package
- **File**: `minica_1.0.0_amd64.deb`
- **Size**: ~18 MB
- **Type**: Native Debian package
- **Installation**: `sudo dpkg -i minica_1.0.0_amd64.deb`
- **Usage**: `minica`

### Tar.gz Package
- **File**: `minica-linux.tar.gz`
- **Size**: ~18 MB
- **Type**: Compressed archive
- **Installation**: `tar -xzf minica-linux.tar.gz && cd minica-linux && ./install.sh`
- **Usage**: `minica`

## Troubleshooting

### Common Issues

#### 1. PyInstaller Build Fails
```bash
# Check Python version
python3 --version

# Reinstall PyInstaller
pip3 uninstall pyinstaller
pip3 install pyinstaller

# Try with --onefile flag
pyinstaller --onefile minica/main.py
```

#### 2. Missing Dependencies
```bash
# Install missing system packages
sudo apt install python3-tk python3-dev

# Install missing Python packages
pip3 install pyOpenSSL cryptography
```

#### 3. AppImage Creation Fails
```bash
# Check if appimagetool is installed
which appimagetool

# Download and install appimagetool
wget https://github.com/AppImage/AppImageKit/releases/download/continuous/appimagetool-x86_64.AppImage
chmod +x appimagetool-x86_64.AppImage
sudo mv appimagetool-x86_64.AppImage /usr/local/bin/appimagetool
```

#### 4. .deb Package Creation Fails
```bash
# Check if dpkg-deb is available
which dpkg-deb

# Install build tools
sudo apt install build-essential
```

### Build Script Issues

#### 1. Permission Errors
```bash
# Make scripts executable
chmod +x build_linux_proper.py
chmod +x install.sh
```

#### 2. Path Issues
```bash
# Use absolute paths
python3 /full/path/to/build_linux_proper.py
```

#### 3. Environment Issues
```bash
# Set environment variables
export PYTHONPATH=/path/to/minica:$PYTHONPATH
export PATH=/path/to/minica:$PATH
```

## Cross-Platform Building

### Using Docker
```bash
# Create Dockerfile
cat > Dockerfile << EOF
FROM ubuntu:20.04
RUN apt update && apt install -y python3 python3-pip python3-tk
COPY . /app
WORKDIR /app
RUN pip3 install -r requirements.txt
RUN python3 build_linux_proper.py
EOF

# Build in Docker
docker build -t minica-builder .
docker run -v $(pwd):/output minica-builder cp -r /app/dist /app/*.AppImage /app/*.deb /app/*.tar.gz /output/
```

### Using WSL (Windows Subsystem for Linux)
```bash
# Install WSL2
wsl --install

# Install Ubuntu
wsl --install -d Ubuntu

# Switch to WSL
wsl

# Follow Linux build instructions
```

## Testing

### Automated Testing
```bash
# Create test script
cat > test_linux_build.sh << EOF
#!/bin/bash
set -e

echo "Testing Linux build..."

# Test executable
if [ -f "dist/minica" ]; then
    echo "✅ Executable created"
    chmod +x dist/minica
else
    echo "❌ Executable not found"
    exit 1
fi

# Test AppImage
if [ -f "MiniCA-x86_64.AppImage" ]; then
    echo "✅ AppImage created"
    chmod +x MiniCA-x86_64.AppImage
else
    echo "❌ AppImage not found"
    exit 1
fi

# Test .deb package
if [ -f "minica_1.0.0_amd64.deb" ]; then
    echo "✅ .deb package created"
else
    echo "❌ .deb package not found"
    exit 1
fi

echo "✅ All tests passed!"
EOF

chmod +x test_linux_build.sh
./test_linux_build.sh
```

## Distribution

### Creating Release Packages
```bash
# Create release directory
mkdir -p release/linux

# Copy packages
cp MiniCA-x86_64.AppImage release/linux/
cp minica_1.0.0_amd64.deb release/linux/
cp minica-linux.tar.gz release/linux/

# Create checksums
cd release/linux
sha256sum * > checksums.txt

# Create release notes
cat > RELEASE_NOTES.md << EOF
# MiniCA Linux Release

## Packages
- MiniCA-x86_64.AppImage - Portable executable
- minica_1.0.0_amd64.deb - Debian package
- minica-linux.tar.gz - Archive package

## Installation
See README.md for installation instructions.

## Checksums
\`\`\`
$(cat checksums.txt)
\`\`\`
EOF
```

## Support

### Getting Help
1. Check this documentation
2. Review error messages carefully
3. Check system requirements
4. Contact support channels

### Contact Information
- **Gorq AI Platforms**: https://gorqai.digital
- **IITCENTER.EU.ORG**: https://iitcenter.eu.org
- **International Internet Trust Center**: https://iitcenter.eu.org

## License

**Proprietary Software License - Public Use Allowed**

This software is distributed under a proprietary license that allows public use while maintaining closed-source protection. See `LICENSE.txt` for complete terms and conditions.

---

**MiniCA Professional Certificate Authority System**  
Copyright © 2024 Gorq AI Platforms & IITCENTER.EU.ORG  
All Rights Reserved  

Published by International Internet Trust Center  
https://iitcenter.eu.org
