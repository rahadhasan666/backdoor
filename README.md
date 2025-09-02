# Reverse Shell Payload Generator
<p align="center"><img src="https://iili.io/KqCOehF.png" alt="project-image"></p>

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

*   **Generator Script (`python3 shell.py`):**
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

*   The **generator script (`python3 shell.py`) can be executed directly within Termux** on Android devices, allowing you to generate payloads on the go.
    *   **Prerequisite:** Install Python in Termux: `pkg install python3`
    *   **Execution:** `python3 shell.py`
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
