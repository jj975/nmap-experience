# nmap-experience

## Installation

### Debian-based Systems
```bash
sudo apt-get update
sudo apt-get install nmap
```
- If you are using Kali Linux, nmap is already installed. Optionally, you can install a graphical shell for nmap called zenmap:
```bash
sudo apt-get update
sudo apt-get install zenmap
```

### Red Hat-based Systems (e.g., CentOS, Fedora)
```bash
sudo yum install nmap
```

### Arch Linux
```bash
sudo pacman -S nmap
```

### macOS (using Homebrew)
```bash
brew install nmap
```

### Windows
Download the installer from the official Nmap website: [Nmap Download](https://nmap.org/download.html)

## Basic Usage

### Scan a Single Host
```bash
nmap 192.168.1.100
```
- or
```bash
nmap hostname
```

### Scan Multiple Hosts
```bash
nmap 192.168.1.1-50
```
- or
```bash
nmap 192.168.1.*
```
- or
```bash
nmap 192.168.1.0/24
```
- or
```bash
nmap 192.168.1.1 192.168.1.100-200
```
- or
```bash
nmap hostname/24
```

### Intensive Scan with Version Detection
```bash
nmap -T4 -A -v 192.168.1.*
```

### TCP and UDP Scan with Service Version Detection
```bash
nmap -sS -sU -T4 -A -v 192.168.1.*
```

### Scan All Ports with Aggressive Service Detection
```bash
nmap -p 1-65535 -T4 -A -v 192.168.1.*
```

### Aggressive Scan with No Ping
```bash
nmap -T4 -A -v -Pn 192.168.1.*
```

### Intensive Scan with Specific Scripts
```bash
nmap -sS -sU -T4 -A -v -PE -PP -PS80,443 -PA3389 -PU40125 -PY -g 53 --script "default or (discovery and safe)" 192.168.1.*
```

### Light Version Detection
```bash
nmap -sV -T4 -O -F --version-light 192.168.1.*
```

### Fast Scan (Top 100 Ports)
```bash
nmap -T4 -F 192.168.1.*
```

### Ping Scan with Traceroute
```bash
nmap -sn --traceroute 192.168.1.*
```

## Interpretation of Results

### Zenmap Buttons

#### Port/Hosts
- View a summary of open ports and hosts.

#### Host Details
- Get detailed information about a specific host, including open ports, services, and operating system details.

#### Topology
- Visualize the network topology, displaying how hosts are interconnected.

### Example Output

#### Basic Host Discovery
```plaintext
Host is up (0.001s latency).
```

#### Port/Hosts
```plaintext
Host: 192.168.1.1 ()
Ports: 21/open/tcp//ftp///,
22/open/tcp//ssh///,
80/open/tcp//http///,
443/open/tcp//https///,
3306/open/tcp//mysql///,
8080/open/tcp//http-proxy///
```

#### Host Details
```plaintext
Open Ports: 22 (ssh), 80 (http), 443 (https)
OS: Linux 2.6.32 - 3.10
```

#### Topology
```plaintext
Host 192.168.1.1 (Router) is connected to:
  - Host 192.168.1.2 (Web Server)
  - Host 192.168.1.3 (Database Server)
```

## Security Considerations

Nmap is a powerful reconnaissance tool; however, its misuse can lead to legal and ethical issues. Always ensure you have proper authorization before scanning any network or system. Unauthorized scanning may be against the law.

Useful resources:
- [Nmap Official Documentation](https://nmap.org/book/man.html)
- [Nmap Scripting Engine](https://nmap.org/book/nse.html)

#### License
- Read the license in the file ./LICENSE
