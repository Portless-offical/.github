# Portless | Enterprise USB Virtualization

Hardware Bridge Over Air.
Virtualize physical USB ports over TCP/IP. Low-latency serial transmission for embedded engineering, remote debugging, and enterprise hardware access.

## About The Project

Portless eliminates the physical constraints of USB connections. Traditional debugging requires you to be tethered to your device. Portless creates a secure, low-latency tunnel that makes a remote USB port behave exactly like a local one.

Whether you are debugging an embedded Linux board in a data center, flashing firmware to a drone in the field, or accessing a legacy serial device from across the globe, Portless bridges the gap.

## Why Portless?

- Native Performance: Built with Rust and Go for bare-metal efficiency. Single binary, zero dependencies.

- E2E Encryption: All traffic is wrapped in TLS 1.3. Your data never leaves the local network unencrypted.

- Auto Discovery: Instant pairing via mDNS. No complex IP configuration required.

- Real-time Serial: Optimized buffer handling for UART/Serial communication with sub-10ms latency.

## Architecture

Portless operates on a Host-Client topology.

```
graph LR
    A[Remote Device (USB)] <-->|Serial/UART| B(Portless Host)
    B <-->|TCP/IP + TLS 1.3| C(Portless Client)
    C <-->|Virtual Port| D[Local Machine]
```


Host Agent: Runs on the device physically connected to the USB hardware (e.g., Raspberry Pi, Industrial PC).

Client Agent: Runs on your workstation. It creates a virtual serial port (e.g., /tmp/ttyVUSB0) that your IDE or terminal connects to.

## Getting Started

### Quick Install (macOS & Linux)

Deploy the latest stable binary using our automated installer:

```bash
curl -fsSL https://raw.githubusercontent.com/Portless-offical/download-center/main/install.sh | sh
```


### Manual Installation

Binaries for Windows, macOS (Intel/Apple Silicon), and Linux (.deb, .rpm, AppImage) are available in our [Download Center](https://github.com/Portless-offical/download-center).

## Usage

On the Host (Device with USB):

```bash
# Share a specific device
portless share --device /dev/ttyUSB0 --auth my-secret-password
```


On the Client (Your Laptop):

```bash
# Connect to the remote device
portless connect --target <HOST_IP> --auth my-secret-password
```


## Roadmap: Portless Cloud (Q1 2026)

We are actively developing a managed relay network to simplify global connectivity.

- Go Global: Access your hardware from anywhere in the world.

- Zero Config: No VPNs, port forwarding, or firewall headaches.

- Managed Security: Fully managed infrastructure with E2E encrypted streams.

- Status: Early Access Waitlist. Pricing targeted at $2/mo.

<p align="center">
<span style="color: #a1a1aa; font-family: monospace;">&copy; 2025 Portless Corporation. All rights reserved.</span>
</p>
