
### ⚙️ MEmu Setup for Android Pentesting

While the Android Studio AVD is a great standard tool, it can be resource-heavy and slow on some machines. **MEmu Play** is a free, high-performance Android emulator for Windows that many penetration testers prefer for its speed, stability, and built-in root features.

**Why MEmu is a great choice for your lab:**
- **Performance:** It's lightweight, fast, and more responsive than the standard AVD, especially on non-specialized hardware.
- **Pre-Rooted:** It allows you to run a rooted environment easily, which is essential for deep testing. Many modern security tools, like dynamic instrumentation frameworks (`Frida`), simply won't work or will be severely limited on a non-rooted device.
- **Convenience:** It provides easy ADB access and simple file sharing between your host and guest operating systems.

Here is the step-by-step guide to getting your MEmu lab environment ready:

#### **Step 1: System Preparation & Installation**
Before you begin, ensure your Windows system meets these requirements:
- **CPU:** A modern 64-bit processor with Intel VT-x or AMD-V virtualization technology enabled in your BIOS/UEFI.
- **RAM:** At least 8 GB (16 GB is highly recommended for a smooth experience).
- **Disk:** 10-20 GB of free space.
You can check if virtualization is enabled by running `systeminfo` in PowerShell and looking for the "Virtualization" lines.

Most guides, including the official one, recommend the following steps:

1.  Download the latest `MEmu-setup.exe` installer from the official website.
2.  Run the installer and follow the on-screen prompts to install MEmu.
3.  MEmu version 9.0.6.1 or newer is generally stable. You may want to avoid auto-updates if a future version introduces instabilities.

#### **Step 2: First Launch & Initial Configuration**
When you launch MEmu for the first time, it will perform a quick setup process. The official guide recommends you adjust its settings for optimal performance.
1.  Click the **Menu (☰)** in the top-right corner and open **Settings**.
2.  Adjust the **CPU cores** and **RAM allocation** based on your PC's specifications. Giving MEmu more resources will make it perform better.
3.  Set your preferred **screen resolution and DPI**.

#### **Step 3: Critical Lab Configurations**
To turn your MEmu instance into a proper pentesting lab, you must enable Root and Debugging.

*   **Enabling Root Access:**
    1.  Go to **Tools** -> **File Manager** on the MEmu home screen.
    2.  Click on the three bars (☰) in the top-left corner, then click the **Settings (gear)** icon.
    3.  Go to **General settings** -> **Advanced** -> **Access Mode** and change it to **"Root Access Mode"**.
    4.  **Important:** Completely close and reopen MEmu for the root access to take effect.

*   **Enabling ADB & Developer Options:**
    1.  Go to the Android **Settings** inside MEmu.
    2.  Scroll down to **"About tablet"** or **"About phone"**.
    3.  Tap (click) on **"Build number"** 7 times until you see a message saying "You are now a developer!".
    4.  Go back to the main settings menu, and you will now see **Developer options**.
    5.  Click into **Developer options** and toggle **"USB debugging" ON**.

#### **Step 4: Connecting MEmu to ADB**
ADB (Android Debug Bridge) is your primary command-line interface for communicating with the emulator—everything from installing APKs to pulling files runs through it.

1.  Ensure the Android Platform Tools are installed on your Windows machine. You can download them from the official Android developer website.
2.  Connect your Windows ADB client to the MEmu instance using the following command:
    ```bash
    adb connect localhost:21503
    ```
3.  The default port for MEmu is **21503**. You can confirm a successful connection by running:
    ```bash
    adb devices
    ```
    You should see `127.0.0.1:21503 device` in the list of attached devices.

#### **Step 5: Installing AndroGoat & Configuring Burp Suite**
*   **Installing the vulnerable app** is now simple. With the `adb` connection active, download the AndroGoat APK and run:
    ```bash
    adb install AndroGoat.apk
    ```
*   **Traffic interception** is a key skill. To route MEmu's traffic through Burp Suite, follow the [proxy configuration instructions in the main guide】. The key difference is that the proxy hostname within the MEmu Wi-Fi settings might need to be your Windows host's IP address (e.g., `10.0.2.2` or `192.168.x.x`), rather than `127.0.0.1`, to properly connect.

This MEmu setup gives you a fast, flexible, and rooted environment that's perfectly suited for the practical exercises we're about to dive into. Use it to work through the OWASP vulnerability examples and get hands-on with the dynamic analysis tools covered in previous sections.
