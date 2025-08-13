    Vertual Machine

### what is a Kernal?

Kernal is the core component of the operating system that  acts as a beidge between the  computer's hardwareand and software,managing resources like the cpu memory and input /output devices.

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20250125094644195811/operating_system_os_.webp" alt="Kernal" style="width: 500px; height: 300px;" />

Where is the Kernel Used?

    In all operating systems: Windows, Linux, macOS, Android, etc.

    When you turn on your computer, the kernel is one of the first things to load.

    Every command or click goes through the kernel to reach the hardware.

🔍 Types of Kernels
Type	Description	Example
Monolithic Kernel	Everything runs in one big block of code	Linux
Microkernel	Only essential parts in kernel; rest run separately	Minix
Hybrid Kernel	Mix of both	Windows, macOS

### What is a Vertual Meachine?

**Virtual Machine** is a space or environment we create to simulate a computer within a computer, where we can install a new operating system.

<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQL4Xz9n8p3On2j-oYh8k2O46UgfcewDnPcqA&s" alt="Virtual machine" style="width: 200px; height: auto;" />

By "space," we mean allocating a portion of the system's RAM and storage (ROM). Once allocated, the new operating system can only access the memory and resources assigned to it.

In essence, we now have two computers running on a single physical machine.

This setup is both safe and practically useful.

### Why where virtual machine?

**Software Testing & Development**

* **Use case:** Test software on different operating systems (Windows, Linux, macOS) without needing multiple physical machines.

**Cybersecurity & Malware Analysis**

* **Use case:** Analyze suspicious files in a safe, isolated environment.

**Server Virtualization**

* **Use case:** Run multiple virtual servers on a single physical server in data centers.

**Cross-Platform Compatibility**

* **Use case:** Use software that’s only available on another OS

**Cloud Computing**

* **Use case:** Every cloud provider (like AWS, Azure, GCP) uses VMs to provide virtual servers (EC2, Compute Engine).

### **Instructions to set up Linux Ubuntu in a Virtual Machine**

**Step 1: Install VirtualBox** - Download the installer from [virtualbox.org]().

**Step 2: Create a New Virtual Machine**

1. Click on **“New”** in VirtualBox.
2. Name your VM (e.g., "Ubuntu").
3. Set **Type** to `Linux` and **Version** to `Ubuntu (64-bit)`.
4. Click  **Next** .

**Step 3: Allocate RAM**

* Choose how much RAM to give your VM.
  * Minimum: **2048 MB (2 GB)**
  * Recommended: **4096 MB (4 GB)** or more
* Click  **Next** .

**Step 4: Create a Virtual Hard Disk**

* Choose  **“Create a virtual hard disk now”** , then click  **Create** .
* Disk file type: Choose **VDI (VirtualBox Disk Image)** → Next.
* Storage on physical hard disk: **Dynamically allocated** → Next.
* Set disk size: **20 GB or more** → Create.

**Step 5: Attach Ubuntu ISO**

1. Select the VM → Click **Settings** → Go to  **Storage** .
2. Under  **Controller: IDE** , click **Empty** → On the right, click the disk icon.
3. Choose **“Choose a disk file”** → Select your downloaded Ubuntu ISO.

**Step 6: Start the VM**

1. Click **Start** to boot the VM.
2. It will boot from the Ubuntu ISO and show the Ubuntu installer.

**Step 7: Install Ubuntu**

1. Choose  **“Install Ubuntu”** .
2. Select language, keyboard layout, and updates as needed.
3. Choose **“Erase disk and install Ubuntu”** (safe — only inside the VM).
4. Follow prompts to:
   * Set your username and password
   * Choose time zone
   * Complete installation

**Step 8: Remove ISO and Reboot**

After installation finishes:

1. The VM will ask to restart → Click  **Restart Now** .
2. It may prompt to  **remove the installation medium** :
   * Go to **Devices > Optical Drives > Remove disk from virtual drive**
   * Then press **Enter**

Step 9: Use Ubuntu 🎉

* You now have a fully working Ubuntu virtual machine.
