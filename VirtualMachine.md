# Setting Up Ubuntu in a Virtual Machine

## What is a Virtual Machine?
A **Virtual Machine (VM)** is a simulated computer environment created within a physical computer. It allows you to run a separate operating system by allocating dedicated portions of your system's RAM and storage (ROM). 

The guest operating system can only access the resources assigned to it, effectively creating two independent computers running on a single physical machine. This approach provides both security and practical advantages.

![Virtual machine interface](https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2014/06/virtualbox-guest-additions.jpg)

## Common Uses of Virtual Machines
### Software Testing & Development
- **Use case:** Test applications across multiple operating systems (Windows, Linux, macOS) without needing separate physical machines.

### Cybersecurity & Malware Analysis
- **Use case:** Safely analyze suspicious files in an isolated environment.

### Server Virtualization
- **Use case:** Run multiple virtual servers on a single physical server in data centers.

### Cross-Platform Compatibility
- **Use case:** Access software that's only available on a different operating system.

### Cloud Computing
- **Use case:** Cloud providers (AWS, Azure, GCP) use VMs to deliver virtual servers (e.g., EC2, Compute Engine).

---

## Step-by-Step Guide: Install Ubuntu in VirtualBox

### Step 1: Install VirtualBox
1. Download VirtualBox from [virtualbox.org](https://www.virtualbox.org/)
2. Run the installer and follow setup instructions

### Step 2: Create a New Virtual Machine
1. Open VirtualBox and click **"New"**
2. Name your VM (e.g., "Ubuntu")
3. Set **Type** to `Linux` and **Version** to `Ubuntu (64-bit)`
4. Click **Next**

### Step 3: Allocate RAM
- **Minimum:** 2048 MB (2 GB)
- **Recommended:** 4096 MB (4 GB) or more
- Click **Next**

### Step 4: Create a Virtual Hard Disk
1. Select **"Create a virtual hard disk now"** → **Create**
2. Choose **VDI (VirtualBox Disk Image)** → **Next**
3. Select **"Dynamically allocated"** → **Next**
4. Set disk size to **20 GB or more** → **Create**

### Step 5: Attach Ubuntu ISO
1. Select your VM → Click **Settings** → Go to **Storage**
2. Under **Controller: IDE**, click **Empty**
3. Click the disk icon → **"Choose a disk file"**
4. Select your downloaded Ubuntu ISO file

### Step 6: Start the VM
1. Click **Start** to boot the VM
2. The system will boot from the Ubuntu ISO and launch the installer

### Step 7: Install Ubuntu
1. Select **"Install Ubuntu"**
2. Configure:
   - Language and keyboard layout
   - Updates (recommended: "Normal installation")
3. Choose **"Erase disk and install Ubuntu"** (safe - only affects the VM)
4. Follow prompts to:
   - Create username/password
   - Set time zone
   - Complete installation

### Step 8: Finalize Installation
1. After installation completes, click **"Restart Now"**
2. When prompted to remove installation media:
   - Go to **Devices > Optical Drives > Remove disk from virtual drive**
   - Press **Enter**

### Step 9: Start Using Ubuntu
- You now have a fully functional Ubuntu virtual machine ready to use!