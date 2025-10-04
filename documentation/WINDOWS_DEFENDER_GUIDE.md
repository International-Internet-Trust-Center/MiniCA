# Windows Defender Exclusion Guide for MiniCA

## Issue
Windows Defender may flag the MiniCA.exe as potentially unwanted software due to:
- PyInstaller packaging
- Cryptographic operations
- File system access

## Solutions

### Method 1: Add Exclusion (Recommended)
1. Open Windows Security
2. Go to Virus & threat protection
3. Click "Manage settings" under Virus & threat protection settings
4. Scroll down to "Exclusions"
5. Click "Add or remove exclusions"
6. Click "Add an exclusion" → "File"
7. Browse to `dist\MiniCA.exe` and select it

### Method 2: Add Folder Exclusion
1. Follow steps 1-6 above
2. Click "Add an exclusion" → "Folder"
3. Select the entire `dist` folder

### Method 3: Temporarily Disable Real-time Protection
1. Open Windows Security
2. Go to Virus & threat protection
3. Click "Manage settings" under Virus & threat protection settings
4. Turn off "Real-time protection" temporarily
5. Run MiniCA.exe
6. Turn Real-time protection back on

### Method 4: Run from Command Prompt
Sometimes running from command prompt works when double-clicking doesn't:
```cmd
cd "C:\path\to\minica\dist"
MiniCA.exe
```

## Why This Happens
- PyInstaller creates self-contained executables that antivirus software may flag
- Cryptographic operations (certificate generation) can trigger security alerts
- The application creates/modifies files which some antivirus software monitors

## Verification
After adding exclusions, the application should run without issues. The MiniCA application is legitimate and safe to use.

## Alternative: Run from Source
If the executable continues to have issues, you can always run from source:
```cmd
python -m minica.main
```
