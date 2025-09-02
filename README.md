Alright, I've made the README.md even more professional, adding more detailed steps, clarifying commands for different OS, and including placeholders for images to illustrate key steps. Remember to replace <!-- IMAGE: [Description of image] --> with the actual image tags when you're ready to add them. code Markdowndownloadcontent_copyexpand_less    # Reverse Shell Payload Generator

[![GitHub stars](https://img.shields.io/github/stars/rahadhasan666/backdoor?style=social)](https://github.com/rahadhasan666/backdoor/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/rahadhasan666/backdoor?style=social)](https://github.com/rahadhasan666/backdoor/network/members)
[![GitHub issues](https://img.shields.io/github/issues/rahadhasan666/backdoor)](https://github.com/rahadhasan666/backdoor/issues)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🚀 Overview

The Reverse Shell Payload Generator is a robust and easy-to-use Python script designed for penetration testers and security enthusiasts. It simplifies the process of creating custom reverse shell payloads for both Windows (PowerShell) and Linux/Unix (Bash) environments. By automating the generation of these critical tools, it allows for quicker setup of listening posts during ethical hacking engagements.

## ✨ Features

*   **Cross-Platform Payload Generation:** Generates highly effective reverse shells for diverse operating systems.
    *   **Windows:** PowerShell-based (`shell.ps1`) for reliable execution.
    *   **Linux/Unix/macOS:** Bash-based (`bash.sh`) for broad compatibility.
*   **Automated Executability:** Automatically sets execute permissions for the Bash script, streamlining deployment.
*   **Clear Listener Instructions:** Provides immediate guidance on how to set up your Netcat listener, ensuring a smooth workflow.
*   **Customizable:** Payloads are dynamically generated based on user-provided LHOST (Local Host IP) and LPORT (Local Port).

## 💡 How It Works

The script operates by taking two essential inputs from the user: your attacking machine's IP address (LHOST) and the port you wish to listen on (LPORT).

1.  **PowerShell Payload (`shell.ps1`):** For Windows targets, a PowerShell script is crafted. This script initiates a TCP connection to your specified LHOST and LPORT. Once connected, it enters a loop to continuously receive commands from your listener, execute them locally on the Windows machine, and relay the command output back over the established TCP stream.
2.  **Bash Payload (`bash.sh`):** For Linux/Unix-like targets, a Bash script is created. This script employs I/O redirection to pipe the standard input, output, and error streams of an interactive Bash shell directly through a TCP connection to your LHOST and LPORT, effectively granting you remote command execution.

<!-- IMAGE: A diagram showing an attacker's machine, the Python script generating payloads, and then two arrows pointing to a Windows target and a Linux target, illustrating the payload types. -->

## 💻 Supported Operating Systems

*   **Generator Script (`reverse_shell_generator.py`):**
    *   Works flawlessly on any system with Python 3 installed:
        *   Windows
        *   Linux (Ubuntu, Debian, Fedora, Arch, etc.)
        *   macOS
        *   Termux (Android)
*   **Generated Payloads:**
    *   `shell.ps1`: Exclusively designed for **Windows** operating systems.
    *   `bash.sh`: Compatible with **Linux/Unix-like** operating systems, including macOS and Android (via Termux).

## 📱 Termux Compatibility (Android)

Great news for mobile penetration testers!

*   The **generator script (`reverse_shell_generator.py`) can be executed directly within Termux** on Android devices, allowing you to generate payloads on the go.
    *   **Prerequisite:** Install Python in Termux: `pkg install python`
    *   **Execution:** `python reverse_shell_generator.py`
*   **Regarding the generated payloads:**
    *   `shell.ps1` (PowerShell) **will NOT function on Termux/Android**, as PowerShell is not a native component of these environments.
    *   `bash.sh` (Bash) **WILL work on Termux/Android**. You can use it to establish a reverse shell *from* your Termux environment *to* your listener. Ensure your `LHOST` is reachable from your Termux device and `LPORT` matches your listener port.

## ⚙️ Installation & Usage Guide

Follow these detailed steps to get started with the Reverse Shell Payload Generator.

### Step 1: Clone the Repository

First, open your terminal or command prompt and clone the repository from GitHub.

**Command:**

```bash
git clone https://github.com/rahadhasan666/backdoor.git
  This command will download the project files into a new directory named backdoor in your current working directory.<!-- IMAGE: Screenshot of the `git clone` command execution in a terminal. -->Step 2: Navigate into the Project DirectoryChange your current directory to the newly cloned backdoor repository.Command: code Bashdownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    cd backdoor
  <!-- IMAGE: Screenshot of the `cd backdoor` command execution, showing the prompt changing. -->Step 3: Ensure Python 3 is InstalledThis script requires Python 3. You can verify your Python version:Command (Linux/macOS/Termux): code Bashdownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    python3 --version
  Command (Windows Command Prompt/PowerShell): code Cmddownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    python --version
  If Python 3 is not installed, please download it from python.org or use your system's package manager:Debian/Ubuntu: sudo apt update && sudo apt install python3Fedora/RHEL: sudo dnf install python3Arch Linux: sudo pacman -S pythonStep 4: Run the Generator ScriptNow, execute the reverse_shell_generator.py script.Command (Linux/macOS/Termux): code Bashdownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    python3 reverse_shell_generator.py
  Command (Windows Command Prompt/PowerShell): code Cmddownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    python reverse_shell_generator.py
  The script will prompt you to enter your LHOST (your attacking machine's IP address) and LPORT (the port you'll use for listening).Example Interaction: code Codedownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    [+] Reverse Shell Payload Generator
[*] Enter your IP address and port to generate the payloads
set lhost: 192.168.1.100  # Replace with your actual IP
set lport: 4444         # Choose your desired port
  <!-- IMAGE: Screenshot of the script running, showing the prompts for LHOST and LPORT, and the user input. -->Step 5: Output and Next StepsUpon successful execution, the script will generate two files (shell.ps1 and bash.sh) and provide instructions for the next steps: code Codedownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    [+] PowerShell payload written to shell.ps1
[+] Bash payload written to bash.sh
[+] Start listener with: nc -lvnp 4444
[!] Execute shell.ps1 on Windows or bash.sh on Linux to get reverse shell
  Step 6: Start Your Netcat ListenerCRITICAL: Before deploying any payload, you MUST set up a listener on your attacking machine (LHOST) to catch the incoming shell connection.Command (Linux/macOS/Termux): code Bashdownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    nc -lvnp <YOUR_LPORT>
# Example: nc -lvnp 4444
  Command (Windows using Netcat for Windows):You might need to download a Netcat binary for Windows. code Cmddownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    nc.exe -lvnp <YOUR_LPORT>
# Example: nc.exe -lvnp 4444
  nc: Netcat utility-l: Listen mode (tells Netcat to listen for incoming connections)-v: Verbose output (provides more information)-n: Numeric-only IP addresses (prevents DNS lookups, speeding up connection)-p: Specifies the port to listen on<!-- IMAGE: Screenshot of a Netcat listener running, showing it waiting for a connection. -->Step 7: Execute Payloads on Target SystemTransfer the appropriate generated payload to your target system and execute it.🎯 On a Windows Target:Transfer shell.ps1 to the Windows machine (e.g., via a web server, USB drive, etc.).Execute it via PowerShell. For more discreet execution or to bypass some restrictions, you might use:Command (PowerShell): code Powershelldownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    powershell.exe -File shell.ps1
  Command (from Command Prompt cmd.exe): code Cmddownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    powershell.exe -NoP -NonI -W Hidden -Exec Bypass -File shell.ps1
  -NoP: No Profile-NonI: Non Interactive-W Hidden: Window Style Hidden (runs without showing a window)-Exec Bypass: Execution Policy Bypass (allows unsigned scripts to run)(Note: Bypassing execution policies might require administrative privileges or specific system configurations. Always understand the context of the target system.)<!-- IMAGE: Screenshot of a Windows command prompt or PowerShell window executing `shell.ps1`. -->🐧 On a Linux/Unix/macOS/Termux Target:Transfer bash.sh to the target machine.Execute it directly. The script already handles making bash.sh executable.Command: code Bashdownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    ./bash.sh
  <!-- IMAGE: Screenshot of a Linux terminal executing `bash.sh`. -->⚠️ Important NoteThis tool is strictly intended for educational purposes, ethical hacking, and authorized penetration testing only. Any unauthorized use, misuse, or deployment against systems for which you do not have explicit permission is illegal and unethical. The creators and maintainers of this tool disclaim any responsibility for illicit use. Always ensure you operate within legal and ethical boundaries.🤝 ContributingContributions are welcome! If you have suggestions for improvements, bug fixes, or new features, please feel free to:Fork the repository.Create a new branch (git checkout -b feature/AmazingFeature).Commit your changes (git commit -m 'Add some AmazingFeature').Push to the branch (git push origin feature/AmazingFeature).Open a Pull Request.📜 LicenseThis project is licensed under the MIT License. See the LICENSE file for full details. code Codedownloadcontent_copyexpand_lessIGNORE_WHEN_COPYING_STARTIGNORE_WHEN_COPYING_END    **Here are the images you requested for the `README.md`:**

**1. Diagram showing an attacker's machine generating payloads for Windows and Linux targets.**
<!-- IMAGE: A diagram showing an attacker's machine, the Python script generating payloads, and then two arrows pointing to a Windows target and a Linux target, illustrating the payload types. -->
  
