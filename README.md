# AWTRIX Civil Protection Alert 🇮🇹

[![GitHub Release](https://img.shields.io/github/v/release/Raythekool/ha-awtrix-dpc-alert?style=flat-square)](https://github.com/Raythekool/ha-awtrix-dpc-alert/releases)
[![GitHub License](https://img.shields.io/github/license/Raythekool/ha-awtrix-dpc-alert?style=flat-square)](LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/Raythekool/ha-awtrix-dpc-alert?style=flat-square)](https://github.com/Raythekool/ha-awtrix-dpc-alert/stargazers)
[![GitHub Issues](https://img.shields.io/github/issues/Raythekool/ha-awtrix-dpc-alert?style=flat-square)](https://github.com/Raythekool/ha-awtrix-dpc-alert/issues)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-Blueprint-41BDF5?style=flat-square&logo=home-assistant)](https://www.home-assistant.io/)
[![AWTRIX](https://img.shields.io/badge/AWTRIX-3-orange?style=flat-square)](https://blueforcer.github.io/awtrix3/)

Blueprint for Home Assistant that displays Italian Civil Protection weather alerts on your AWTRIX3 device.

## ⚠️ Requirements

Before using this blueprint, make sure you have:

1. **Home Assistant** with blueprint support
2. **AWTRIX 3** device configured and connected via MQTT
3. **DPC Alert Integration** installed from [caiosweet/Home-Assistant-custom-components-DPC-Alert](https://github.com/caiosweet/Home-Assistant-custom-components-DPC-Alert)

## 📦 Installation

### Main Blueprint

### Method 1: Automatic Import (recommended)

1. Click the button below to import the blueprint:

   [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FRaythekool%2Fha-awtrix-dpc-alert%2Fblob%2Fmain%2Fawtrix_dpc_alert.yaml)

2. Click "Import Blueprint" in your Home Assistant
3. The blueprint will be available in your automations

### Method 2: Manual Import

1. Go to Home Assistant → Settings → Automations & Scenes → Blueprints
2. Click the "Import Blueprint" button
3. Enter this URL:

   ```text
   https://github.com/Raythekool/ha-awtrix-dpc-alert/blob/main/awtrix_dpc_alert.yaml
   ```

4. Click "Preview" and then "Import Blueprint"

### Method 3: Local File

1. Download the `awtrix_dpc_alert.yaml` file
2. Copy the file to the `blueprints/automation/` folder in your Home Assistant configuration
3. Restart Home Assistant or reload automations

## 🎨 Icon Setup

For better visualization, upload the recommended icon to your AWTRIX device. See the [Icons Upload Guide](ICONS_UPLOAD.md) for details.

**Recommended icon:**
- **dpc-warning** (16754) - Alert icon for all risk types

The guide includes an automatic upload script with simple usage.

## 🚀 Usage

1. Go to Home Assistant → Settings → Automations & Scenes
2. Click "Create Automation" → "Use a blueprint"
3. Select "AWTRIX Civil Protection Alert 🇮🇹"
4. Configure the parameters:
   - **AWTRIX Device**: Select your AWTRIX device
   - **DPC Alert Sensors**: Select the alert sensors to monitor
   - **Minimum Alert Level**: Set the minimum level (0-4)
     - 0 = Show all alerts
     - 1 = Green (Ordinary criticality)
     - 2 = Yellow (Moderate criticality)
     - 3 = Orange (High criticality)
     - 4 = Red (Extreme criticality)
   - **Message Duration**: Display time for custom app in seconds (default: 20)
   - **Notification Duration**: Display time for notifications in seconds (default: 10)
   - **Alert Icon**: Customize icon name (default: dpc-warning)
   - **Enable Sound**: Toggle sound notifications
   - **Sound Level**: Minimum alert level to play sound (default: Orange/High)
   - **Rainbow Text Level**: Minimum alert level for rainbow text effect (0-4, default: 0 = disabled)
   - **Display Mode**: Choose how to display alerts:
     - Custom App (Persistent): Stays on screen until cleared
     - Notification (Temporary): Pop-up that auto-dismisses or holds based on duration
     - Both: Send both custom app and notification
   - **Test Mode**: Enable to manually trigger test alerts without waiting for real DPC data
5. Save the automation

### 🧪 Testing Your Setup

The blueprint includes built-in test mode:

1. Edit your automation
2. Enable "Test Mode"
3. Set test levels for each risk type:
   - **Hydraulic Risk Level**: 0-4 (0 = disabled)
   - **Storm Risk Level**: 0-4 (0 = disabled)
   - **Hydrogeological Risk Level**: 0-4 (0 = disabled)
4. Save and trigger the automation manually
5. You should see the test alert on your AWTRIX device

Example: Setting Hydraulic=3 and Storm=4 will display "IDR3-TMP4" with red color (highest level).

## 🎯 Features

- **Multi-sensor monitoring**: Supports multiple DPC sensors simultaneously
- **Criticality filter**: Shows only alerts above a certain level
- **Automatic colors**: Messages are colored based on criticality level (vivid colors)
  - Blue: No alert
  - Green: Ordinary
  - Yellow: Moderate
  - Dark Orange: High
  - Red: Extreme
- **Compact display**: Shows abbreviated alerts (e.g. "IDR3-TMP4") for both apps and notifications
- **Rainbow text effect**: Configurable rainbow text animation for high-severity alerts
- **Customizable icon**: Single icon for all alert types (GIF format recommended)
- **Sound notifications**: Optional sound alerts for critical warnings with configurable threshold
- **Display modes**: Choose between Custom App (persistent), Notification (temporary), or Both
- **Flexible duration**: Separate durations for custom apps and notifications
- **Hold mode**: Notifications with duration 0 stay on screen until manually dismissed
- **Multi-device**: Supports multiple AWTRIX devices simultaneously
- **Auto-clear**: Automatically removes alerts when they are no longer active
- **Test mode**: Built-in test mode to verify configuration without waiting for real alerts

## 📺 Display Format

Both Custom App and Notification use compact format showing all active alerts on one screen:

**Example: IDR3-TMP4**
- **IDR** = Rischio Idraulico (Hydraulic) level 3
- **TMP** = Rischio Temporali (Storm) level 4
- Color is based on highest alert level (red in this case)

**Abbreviations:**
- **IDR** = Rischio Idraulico (Hydraulic)
- **TMP** = Rischio Temporali (Storm)
- **IDG** = Rischio Idrogeologico (Hydrogeological)

## 🔧 Advanced Configuration

### Customizing Message Duration

The blueprint provides two duration settings:

- **Message Duration**: Controls display time for custom apps (persistent mode)
  - `0` = use the device's global time setting
  - `1-300` = specific seconds (maximum 5 minutes)

- **Notification Duration**: Controls display time for notifications
  - `0` = hold mode (notification stays until manually dismissed via middle button)
  - `1-300` = auto-dismiss after specified seconds

### Display Modes

The blueprint supports three display modes:

- **Custom App (Persistent)**: Alert stays on AWTRIX as a persistent app until cleared
  - Published to MQTT topic `{prefix}/custom/dpc_alert`
  - Uses message_duration setting
  - Ideal for ongoing alerts you want to monitor continuously

- **Notification (Temporary)**: Pop-up notification that appears immediately
  - Published to MQTT topic `{prefix}/notify`
  - Uses notification_duration setting
  - When duration is 0, includes `hold: true` (dismiss with middle button)
  - Ideal for immediate attention alerts

- **Both**: Sends both custom app and notification simultaneously
  - Maximum visibility for critical alerts
  - Custom app persists while notification provides immediate pop-up

### Visual Effects

The blueprint provides configurable rainbow text effect:

- **Rainbow Text Effect** (rainbow_level setting):
  - Applies colorful rainbow animation to alert text
  - Default: 0 (disabled)
  - When enabled, overrides the solid color setting
  - Set to desired minimum alert level (1-4) to enable for that level and above
  - Note: Rainbow and color are mutually exclusive (AWTRIX API limitation)

**Customization Examples:**
- Disable effects: Set rainbow_level to 0
- Maximum effects: Set rainbow_level to 1 (enables for all alerts)
- Extreme only: Set rainbow_level to 4 (Red alerts only)

### Using Custom Icons

You can use any icon from LaMetric or upload custom ones to your AWTRIX `/ICONS/` folder. Enter the icon filename (without extension) in the icon field. The blueprint references icons by name, not by LaMetric ID.

**Icon format:** GIF format is recommended for best compatibility with AWTRIX.

For detailed instructions on uploading icons, see the [Icons Upload Guide](ICONS_UPLOAD.md).

## 📝 Notes

- The blueprint uses "restart" mode to avoid duplicates when multiple alerts arrive
- Custom apps are published to MQTT topic `{prefix}/custom/dpc_alert`
- Notifications are published to MQTT topic `{prefix}/notify`
- Multiple active alerts are displayed in compact format on one screen (e.g. "IDR3-TMP4")
- Rainbow text effect is configurable with level threshold (default: disabled)
- Rainbow and color are mutually exclusive per AWTRIX API (rainbow takes precedence when enabled)
- Icon file should be in GIF format and uploaded to AWTRIX `/ICONS/` folder
- Notifications with duration=0 automatically use hold mode (manual dismiss required)
- Test mode allows manual testing without waiting for real DPC alerts

## 🤝 Contributing

Contributions, bug reports, and feature requests are welcome! Feel free to open an issue or pull request.

## 📄 License

This project is distributed under the MIT License. See the `LICENSE` file for more details.

## 🙏 Credits

- DPC Alert Integration: [caiosweet](https://github.com/caiosweet/Home-Assistant-custom-components-DPC-Alert)
- AWTRIX 3: [Blueforcer](https://github.com/Blueforcer/awtrix3)
- Inspiration from flow: [Blueforcer Flow](https://flows.blueforcer.de/flow/rM3xOBxvA8Lz#)
