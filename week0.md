# Open Source Tools

### what is Software?

In a computer system, the software is basically a set of instructions that tell a computer to do a specific task that serves its users.

* A software is not a physical thing like hardware, it rather makes the hardware work as per user requirements by giving instructions.

### **what are open source tools?**

Open source tools are software with publicly available source code which can be use for free of cost, That is a thing but the point of open source softwars or tools are all about **freedom.**

By this, I mean the freedom for user and developers do much more with open source software.
In this softwares you can able to create feachers, report the bugs and also fix them.
which make you as contrebuter of that software.

![1753677044602](https://file+.vscode-resource.vscode-cdn.net/c%3A/projects/OpenSource/image/week0/1753677044602.png)

Previously most of the large software projects happend in side the private companies.
they sell thir proprietary software, typically with after sales support, Interest in open source started in early 80s.
But, the Exponential growth happened after Linux.

![1753636502787](https://file+.vscode-resource.vscode-cdn.net/c%3A/projects/OpenSource/image/week0/1753636502787.png)
That is the point where two approaches, mixing proprietary software with open source.
Red Hat is one the best known example with Red Hat Enterprise Linux, or RHEL.
But RHEL has open source counterpart called centerOS.

<img src="image/week0/1753677392046.png" alt="Red Hat" style="width: 500px; height: auto;" />

### **Are Open-Source Tools Secure?**

Yes, open-source tools can be secure. While the source code is publicly available, this does not mean it is insecure. In fact, open-source software often benefits from having a large and active community of developers and users.

Because many eyes are reviewing the code, vulnerabilities can be identified and resolved quickly. When bugs or security issues are reported, contributors from around the world often collaborate to fix them faster than in closed-source software, where only a limited number of developers have access to the code.

However, like any software, open-source tools must be used responsibly:

Always use well-maintained and trusted projects.

* Keep dependencies updated.
* Watch for security advisories.

### **Example**

* **GIMP** : A powerful cross-platform imageeditor favored by photographers and graphic designers.
* **VLC Media Player** : A popular multimediplayer supporting nearly all audio and video formats with hardware
* **Shotcut** : Advanced open-source video editing software used for non-destructive editing and wide format support
* **Linux** : The most in-demand open-source operating system known for its security, flexibility, and community support, running desktops and many devices.
* **Git** : The world's most popular distributed version control system, critical for software development and open-source collaboration.
* **Apache Hadoop and Apache Spark** : Leading open-source big data platforms for distributed data processing and analytics, widely used in enterprise data environments **.**
* **Jupyter Notebook** : An interactive computing environment popular in data science and education for combining code, visualizations, and text.
* **Docker and Kubernetes** : Dominant open-source tools for containerization and orchestration to build scalable cloud-native applications.
* **Grafana and Prometheus** : Widely used for monitoring, alerting, and data visualization in IT and IoT systems.

### **🖥️ Common CLI Commands: Windows vs Linux**

| #  | **Action**            | **Windows CMD Command**   | **Linux Bash Equivalent**   |
| -- | --------------------------- | ------------------------------- | --------------------------------- |
| 1  | Change directory            | `cd <directory>`              | `cd <directory>`                |
| 2  | List directory contents     | `dir`                         | `ls`                            |
| 3  | Create a directory          | `mkdir <directory>`           | `mkdir <directory>`             |
| 4  | Remove a directory          | `rmdir <directory>`           | `rmdir <directory>` or rm -r    |
| 5  | Delete a file               | `del <filename>`              | `rm <filename>`                 |
| 6  | Copy a file                 | `copy <source> <destination>` | `cp <source> <destination>`     |
| 7  | Move a file                 | `move <source> <destination>` | `mv <source> <destination>`     |
| 8  | Rename a file               | `rename <oldname> <newname>`  | `mv <oldname> <newname>`        |
| 9  | Display a message           | `echo <message>`              | `echo <message>`                |
| 10 | Ping a host                 | `ping <hostname>`             | `ping <hostname>`               |
| 11 | Clear screen                | `cls`                         | `clear`                         |
| 12 | Display IP configuration    | `ipconfig`                    | `ifconfig` or `ip a`          |
| 13 | List running tasks          | `tasklist`                    | `ps aux` or `top`             |
| 14 | Kill a running process      | `taskkill /IM <process-name>` | `killall <process-name>`        |
| 15 | Disk check                  | `chkdsk <drive>:`             | `fsck` (run on unmounted disks) |
| 16 | System file checker         | `sfc /scannow`                | `sha256sum`/manual checks       |
| 17 | Shutdown system immediately | `shutdown /s /f /t 0`         | `shutdown now` or `poweroff`  |
| 18 | Restart system              | `shutdown /r /f /t 0`         | `reboot`                        |

### Install VM(Virtual Machine)?

**Virtual Machine (VM)** is one of the best ways to work with open-source tools — especially Linux — without affecting the host system. It provides a safe, isolated environment to experiment, break things, and learn.

* **VirtualBox** (free and open-source)

  * Website: [https://www.virtualbox.org/](https://www.virtualbox.org/ "virtualbox")
* **Linux ISO** (Ubuntu is highly recommended for beginners)

  * Ubuntu: [https://ubuntu.com/download/desktop/](https://ubuntu.com/download/desktop "ubuntu")
