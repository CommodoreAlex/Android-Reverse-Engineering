# Android Emulator Setup for Penetration Testing (Windows)

This guide helps penetration testers set up an Android Virtual Device (AVD) using Android Studio on Windows. AVDs are essential for mobile app testing, reverse engineering, and dynamic analysis in a controlled lab environment.

---

## Step-by-Step Installation

### 1. Install Android Studio

Download and install Android Studio from the official site:
```text
https://developer.android.com/studio
```

During setup:

- Choose **Standard installation**.

- Ensure the Android Virtual Device (AVD) and SDK components are included.

![image](https://github.com/user-attachments/assets/b567550f-33ce-46bc-a5e1-09aaa46b7fe7)


---

### 2. Launch Android Studio & Create a New Project

You don’t need to build an actual app—just create a dummy project to access the Device Manager.

- Select: `New Project → Empty Activity`

![image](https://github.com/user-attachments/assets/3ae7f804-daee-4042-bd99-9dcf2dd6e9f6)


- Name it anything (e.g., `TestAVD`)

- Finish the setup and you will see the project window:

![image](https://github.com/user-attachments/assets/f39d7ee2-52a1-4154-b538-a330609f0716)


---

### 3. Open AVD Manager

From the top menu:
```text
Tools → Device Manager
```

Then:

- Click **"Create device"**


---

### 4. Configure Your Virtual Device

1. **Choose a hardware profile**

- Recommended: `Pixel 4` or `Pixel 3a`

2. Click **Next**


---

### 5. Select a System Image

> Important for Pentesting: Choose a **Google APIs** image, **not** one with Google Play Store.

- Architecture: `x86_64`

- API Level: 30–33

- Example: `Tiramisu (API 33) - x86_64 - Google APIs`

![image](https://github.com/user-attachments/assets/daf2e3f0-f945-4714-b6f7-bd0cf47d6a4c)

Click **Download** → After install → Click **Next**:

![image](https://github.com/user-attachments/assets/6e778f8a-6f0f-4519-b85f-69c38432ab96)


---

### 6. Finalize Virtual Device

- Name it (e.g., `Pixel4_API33_Test`)
    
- Set **Graphics** to `Hardware` (if supported)
    
- Finish the wizard
    

---

### 7. Launch the Emulator

From the **Device Manager**, click the green ▶️ Play button:

![image](https://github.com/user-attachments/assets/3acccdcf-54e8-4f26-8323-3b2296f66fbf)


Once launched, the emulator boots into Android OS:

![image](https://github.com/user-attachments/assets/304e936c-772b-4251-9c01-c759dd91cb1e)


---

## Post-Setup Tips for Penetration Testers

### Enable ADB Root Access (if supported)

In terminal:
```bash
adb devices adb root adb remount
```

This enables you to:
- Push tools like Frida

- Modify file systems

- Bypass root detection

---

### Suggested Tools for Testing

|Tool|Purpose|
|---|---|
|`adb`|CLI interaction with emulator|
|`Burp Suite`|Intercept HTTPS traffic|
|`MobSF`|Static + dynamic analysis|
|`Frida`|Runtime instrumentation|
|`APKTool`|Decompile and recompile APKs|
|`JADX`|Convert APKs to Java source|
|`Magisk`|Root management framework|

---

## Recommendations

- **Avoid Google Play system images**: They prevent root access.

- **Run natively on host OS**: Do not run Android Emulator inside a Virtual Machine—nested virtualization is slow and often incompatible.

- **Snapshot often**: Save emulator states to revert if something breaks.

---
