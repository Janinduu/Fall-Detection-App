# 📱 Fall Detection Android Application

<div align="center">

**An intelligent Android application that detects falls using device sensors and sends automatic SMS alerts to emergency contacts.**

[📥 Download APK](#installation) -  [📖 Documentation](#documentation) -  [🐛 Report Bug](../../issues) -  [💡 Request Feature](../../issues)

</div>

---

## 🌟 Features

<table>
<tr>
<td width="50%">

### 🔍 **Core Functionality**
- 📊 **Real-time sensor monitoring** using accelerometer and gyroscope
- 🧠 **Intelligent fall detection algorithm** with multi-phase validation
- 📱 **Automatic SMS alerts** with location data to emergency contacts
- ⚙️ **Background service** for continuous monitoring

</td>
<td width="50%">

### 🎨 **User Experience**
- 🎨 **Modern Material Design UI** with accessibility compliance
- ⚡ **Configurable sensitivity settings** and alert preferences
- 🧪 **Test functionality** for verifying system operation

</td>
</tr>
</table>

---

## 📋 Table of Contents

- [🚀 Quick Start](#-quick-start)
- [⚙️ Installation](#️-installation)
- [📱 Usage Guide](#-usage-guide)
- [🔧 Configuration](#-configuration)
- [🧠 Algorithm Details](#-algorithm-details)
- [🛠️ Troubleshooting](#️-troubleshooting)
- [📊 Technical Specifications](#-technical-specifications)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

---

## 🚀 Quick Start

### Prerequisites

<details>
<summary>📋 Click to expand prerequisites checklist</summary>

- [ ] **Android Studio** (latest stable version)
- [ ] **Android SDK** with API level 26 or higher
- [ ] **Physical Android device** with accelerometer sensor
- [ ] **Java 11** or higher
- [ ] **Active mobile network** for SMS functionality

</details>

### 🔧 Installation

1. **Clone the repository**
git clone [RepoName]
cd fall-detection-app

2. **Open in Android Studio**
- Launch Android Studio
- Select "Open an existing Android Studio project"
- Navigate to the cloned folder

3. **Sync dependencies**
// Verify these dependencies in build.gradle.kts
implementation("androidx.cardview:cardview:1.0.0")
implementation("androidx.preference:preference:1.2.1")
implementation("androidx.work:work-runtime:2.9.0")
implementation("com.google.android.gms:play-services-location:21.0.1")

4. **Enable Developer Options on your device**
- Go to `Settings` → `About Phone`
- Tap `Build Number` 7 times
- Enable `USB Debugging` in Developer Options

5. **Build and Install**
- Connect your device via USB
- Click the Run button in Android Studio

---

## 📱 Usage Guide

### 🏠 Main Screen Interface

<table>
<tr>
<td width="33%">

#### 🟢 Fall Detection Status
- **Status Indicator**: Shows "ACTIVE" (green) or "INACTIVE" (red)
- **Toggle Switch**: Enable/disable monitoring
- **Real-time Display**: Live sensor readings

</td>
<td width="33%">

#### 📊 Sensor Data Display
- **Accelerometer**: X, Y, Z coordinates (m/s²)
- **Gyroscope**: X, Y, Z rotation rates (rad/s)
- **Live Updates**: Values change with device movement

</td>
<td width="33%">

#### 🎛️ Control Panel
- **Settings Button**: Access configuration
- **Test Button**: Simulate fall detection
- **Emergency Override**: Manual alert trigger

</td>
</tr>
</table>

### ⚙️ Settings Configuration

<details>
<summary>📞 Emergency Contact Setup</summary>

1. Navigate to Settings screen
2. Enter emergency contact phone number (include country code)
3. Use "Test SMS" button to verify configuration
4. Save settings before exiting

**Example format**: `+1234567890`

</details>

<details>
<summary>🔔 Alert Preferences</summary>

- **SMS Alerts**: Enable/disable automatic notifications
- **Vibration**: Toggle haptic feedback
- **Sensitivity**: Adjust detection threshold (Very Low to Very High)

</details>

---

## 🧠 Algorithm Details

### 🔍 Three-Phase Detection Process

The fall detection algorithm uses a sophisticated three-phase approach:

1. **🔍 Free Fall Detection** - Monitors for low acceleration periods (<2.0 m/s²)
2. **💥 Impact Detection** - Identifies high acceleration events (>30.0 m/s²)
3. **⏸️ Inactivity Confirmation** - Verifies motionlessness after impact (<2.0 m/s²)

### 📊 Detection Thresholds

| Parameter | Value | Description |
|-----------|-------|-------------|
| `FALL_THRESHOLD` | 30.0 m/s² | Impact detection threshold |
| `INACTIVITY_THRESHOLD` | 2.0 m/s² | Post-fall stillness detection |
| `IMPACT_WINDOW` | 750ms | Impact detection time window |
| `INACTIVITY_WINDOW` | 2000ms | Inactivity confirmation period |
| `COOLDOWN_PERIOD` | 30s | Prevents duplicate alerts |

### 🧮 Mathematical Implementation
// Magnitude calculation
magnitude = √(x² + y² + z²)

// Buffer system maintains 10 recent readings
private static final int BUFFER_SIZE = 10;
private float[][] accelBuffer = new float[BUFFER_SIZE];


---

## 🛠️ Troubleshooting

<details>
<summary>❌ Sensor Data Not Updating</summary>

**Possible Causes & Solutions:**
- ✅ Check if device has required sensors
- 🔄 Restart the device to clear sensor cache
- 🔐 Verify all permissions are granted
- 🔋 Disable battery optimization for the app
- 📱 Test on different device if available

</details>

<details>
<summary>📵 SMS Alerts Not Sending</summary>

**Troubleshooting Steps:**
- 📞 Verify phone number format (include country code)
- 📶 Check mobile network connection
- 🧪 Use "Test SMS" button in settings
- 🔐 Confirm SMS permission is granted
- 💳 Check if device has SMS credits/plan

</details>

<details>
<summary>💥 App Crashes on Startup</summary>

**Common Solutions:**
- 🔄 Update Android Studio to latest version
- 🧹 Clean and rebuild project (`Build` → `Clean Project`)
- 📱 Verify device compatibility (Android 8.0+ required)
- 📋 Check Logcat for specific error messages
- 🔧 Verify all dependencies are properly synced

</details>

<details>
<summary>⚖️ Fall Detection Sensitivity Issues</summary>

**Adjustment Guidelines:**
- 📉 **Too Sensitive**: Lower sensitivity slider setting
- 📈 **Not Sensitive Enough**: Increase sensitivity setting
- 📍 **Device Placement**: Recommend waist or chest mounting
- 🧪 **Testing**: Use "Test Fall Detection" button
- 👤 **User Activity**: Consider individual movement patterns

</details>

---

## 📊 Technical Specifications

### 🎯 System Requirements

| Requirement | Specification |
|-------------|---------------|
| **Android Version** | 8.0 (API 26) or higher |
| **Target SDK** | API 35 (Android 14) |
| **Required Sensors** | Accelerometer (mandatory) |
| **Optional Sensors** | Gyroscope (enhances accuracy) |
| **Storage** | 50MB available space |
| **Network** | Mobile network for SMS |

### 🔐 Required Permissions

<table>
<tr>
<td width="50%">

#### Essential Permissions
- `SEND_SMS` - Emergency alert messages
- `ACCESS_FINE_LOCATION` - GPS coordinates
- `ACCESS_COARSE_LOCATION` - Fallback location
- `VIBRATE` - Haptic feedback

</td>
</tr>
</table>

### 🏗️ Project Structure

app/
├── 📁 manifests/
│ └── AndroidManifest.xml
├── 📁 java/com.example.test01/
│ ├── MainActivity.java
│ ├── SettingsActivity.java
│ ├── SensorService.java
│ ├── FallDetectionAlgorithm.java
│ ├── SMSManager.java
│ ├── SharedPreferencesHelper.java
│ └── SMSReceiver.java
├── 📁 res/
│ ├── 📁 drawable/
│ ├── 📁 layout/
│ ├── 📁 menu/
│ └── 📁 values/
└── build.gradle.kts


### 🔬 Test Scenarios

- [x] **Sensor Availability Check** - Verify accelerometer/gyroscope presence
- [x] **Fall Simulation** - Test algorithm with controlled movements
- [x] **SMS Delivery** - Confirm emergency alerts reach contacts
- [x] **Background Operation** - Validate continuous monitoring

