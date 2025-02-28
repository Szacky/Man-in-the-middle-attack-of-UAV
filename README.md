# Drone Control Package Sender (with MITM Considerations)

This repository contains a Python script for sending various control packets to a drone via UDP. It allows users to unlock the drone, initiate takeoff, land, or send both unlock and takeoff commands. While this script demonstrates basic drone control, it can also be a target for **Man-in-the-Middle (MITM)** attacks.

> **Disclaimer**: This script is intended for educational purposes only. Unauthorized use of this tool to attack or disrupt real systems or devices is illegal and unethical. Always ensure you have explicit consent before performing any security tests.

## Features

- **Unlock the drone**: Sends a specific unlock command to allow control of the drone.
- **Takeoff**: Sends a command for the drone to take off.
- **Land**: Sends a landing command to bring the drone back to the ground.
- **Unlock & Takeoff**: A combination of both unlock and takeoff commands.

## MITM Vulnerability

### Security Risks:
- The script sends raw **UDP packets**, which can be intercepted by an attacker between the sender and receiver. Attackers can capture, modify, or replay packets, potentially gaining control over the drone or disrupting its operation.

### Packet Sniffing:
- MITM attackers can intercept the UDP traffic, read the control commands, and either observe or manipulate them.

### Packet Injection:
- An attacker could inject malicious packets into the communication, causing the drone to act unexpectedly (e.g., malicious takeoff, landing, or unlocking).

## How to Mitigate MITM Attacks

- **Encryption**: Use encryption (e.g., **TLS** or **DTLS**) to secure the communication between the control system and the drone.
- **Authentication**: Ensure that both the sender and receiver authenticate each other to prevent unauthorized entities from controlling the drone.
- **Integrity Checks**: Implement cryptographic hash functions to verify packet integrity and ensure the packets have not been tampered with.

## Usage

1. **Modify the IP Address and Port**: Edit the script to reflect the correct IP address (`your address`) and port (`your port`) of your setup.
2. **Run the Script**: After modifying the configuration, run the script. You will be prompted to select the desired action:
    - `1`: Unlock the drone
    - `2`: Initiate takeoff
    - `3`: Land the drone
    - `4`: Unlock and takeoff in sequence

### Example:

```bash
python drone_control.py
