# 🎨 Icons Upload Guide

## Recommended Icon

For better visualization, upload this icon to your AWTRIX:

- **dpc-warning** (16754) - Alert icon for all risk types

**Important:** AWTRIX supports GIF format icons. The upload script automatically prioritizes downloading GIF versions over PNG format for better compatibility.

You can find more icons at [developer.lametric.com/icons](https://developer.lametric.com/icons) or create custom ones.

## 📤 Automatic Script to Upload Icon

We've included a script that automatically downloads the recommended icon from LaMetric and uploads it to your AWTRIX device.

### Easiest method - Just run the script

```bash
# Linux/Mac - prompts for IP
./upload_icons.sh

# Windows - prompts for IP
upload_icons.bat

# Or use Python directly
python3 upload_icons.py
```

When you run the script without any parameters, it will:

1. Prompt you to enter your AWTRIX device IP address
2. Automatically download the recommended DPC icon from LaMetric
3. Upload it to your AWTRIX device

### Quick usage with IP address

```bash
# Provide IP address directly (Linux/Mac)
./upload_icons.sh 192.168.1.100

# Provide IP address directly (Windows)
upload_icons.bat 192.168.1.100

# Or use Python directly
python3 upload_icons.py 192.168.1.100
```

### Advanced options

```bash
# Upload a custom icon instead of default
./upload_icons.sh 192.168.1.100 --icon my-custom-icon 12345

# Upload default plus additional custom icon
./upload_icons.sh 192.168.1.100 --default-icons --icon extra-icon 99999
```

### What the script does

- Downloads icon from LaMetric's public icon library (prioritizes GIF format)
- Converts and uploads it to your AWTRIX device `/ICONS/` folder via HTTP API
- No additional dependencies needed - uses only Python 3 standard library with requests module
- Works on Linux, Mac, and Windows

The script automatically downloads icons from LaMetric and uploads them to your AWTRIX via HTTP. No additional dependencies are needed, it only uses Python 3 standard library.

## Using Custom Icons

You can use any icon from LaMetric or upload custom ones to your AWTRIX `/ICONS/` folder. Enter the icon filename (without extension) in the blueprint configuration. The blueprint references icons by name, not by LaMetric ID.

**Icon format:** GIF format is recommended for best compatibility with AWTRIX.
