# Reverse Shell Payload Generator

This is a simple Python script that generates PowerShell and Bash reverse shell payloads, tailored to your specified IP address and port. It automates the creation of `shell.ps1` (for Windows) and `bash.sh` (for Linux) files, making it easier to set up reverse shell listeners for penetration testing or ethical hacking exercises.

## How it Works

The script takes your Local Host (LHOST) IP address and Local Port (LPORT) as input.

1.  **PowerShell Payload (for Windows):** It generates a PowerShell script (`shell.ps1`) that establishes a TCP connection to your LHOST and LPORT. Once connected, it continuously reads commands from the listener, executes them, and sends the output back to the listener.
2.  **Bash Payload (for Linux/Unix):** It generates a Bash script (`bash.sh`) that redirects the standard input, output, and error streams of a Bash interactive shell to a TCP connection established with your LHOST and LPORT.

## Features

*   Generates PowerShell reverse shell for Windows.
*   Generates Bash reverse shell for Linux/Unix.
*   Automatically makes the `bash.sh` script executable.
*   Provides clear instructions for starting your Netcat listener.

## Supported Operating Systems

*   **Generator Script:** This Python script can be run on any operating system that has Python 3 installed (Windows, Linux, macOS).
*   **Generated Payloads:**
    *   `shell.ps1`: Designed to be executed on **Windows** operating systems.
    *   `bash.sh`: Designed to be executed on **Linux/Unix** operating systems, including macOS.

## Termux Compatibility (Android)

Yes, the **generator script itself can run on Termux**.

To run the generator script on Termux:

1.  **Install Python:**
    ```bash
    pkg install python
    ```
2.  **Run the script:**
    ```bash
    python reverse_shell_generator.py # assuming you saved the script as reverse_shell_generator.py
    ```

However, regarding the **generated payloads**:

*   `shell.ps1` (PowerShell) **will NOT work directly on Termux/Android** as PowerShell is not natively available.
*   `bash.sh` (Bash) **WILL work on Termux/Android** if you want to get a reverse shell *from* your Termux environment *to* another listener. Just ensure you set the `LHOST` to an IP address reachable from your Termux device and `LPORT` to your listener port.

## Installation and Usage

### 1. Clone the Repository

First, you need to clone the repository from GitHub.

```bash
git clone https://github.com/rahadhasan666/backdoor.git
