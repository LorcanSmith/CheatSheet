
# 🧠 Nmap Cheat Sheet

## 🔍 Basic Scan

```bash
nmap <IP>
```
## 💨 Fast Scan for THM
```bash
sudo nmap -sS -p- -vv <IP>
```
## 🔧 More Advanced Scan

```bash
nmap -sV -sC -p- -oN <output.txt> <IP>
```

- `-sV` → Service version detection  
- `-sC` → Run default NSE scripts  
- `-p-` → Scan all 65535 ports  
- `-oN` → Output results in normal format

📄 [Nmap Cheat Sheet (Comparitech PDF)](https://cdn.comparitech.com/wp-content/uploads/2019/06/Nmap-Cheat-Sheet.pdf)

---

## 🔌 Port Scan Types

| Type              | Command                          |
|-------------------|----------------------------------|
| TCP Connect Scan  | `nmap -sT <IP>`                  |
| TCP SYN Scan      | `sudo nmap -sS <IP>`             |
| UDP Scan          | `sudo nmap -sU <IP>`             |

---

## ⚙️ Scan Options

| Option              | Description                              |
|---------------------|------------------------------------------|
| `-p-`               | Scan all ports                           |
| `-p1-1023`          | Scan ports 1 to 1023                     |
| `-F`                | Fast scan (100 most common ports)       |
| `-r`                | Scan ports in consecutive order         |
| `-T<0-5>`           | Set timing template (0 = slow, 5 = fast) |
| `--max-rate <n>`    | Max packets/sec                         |
| `--min-rate <n>`    | Min packets/sec                         |
| `--min-parallelism` | Minimum concurrent probes               |
| `--reason`          | Show reason a port is considered open   |

---

## 🎯 Advanced Scan Types

- **Null Scan**  
- **FIN Scan**  
- **Xmas Scan**  
- **TCP Maimon Scan**  
- **TCP ACK Scan**

---

## 🕵️ Spoofing / Evasion

- **Fragmented Packets**:
  ```bash
  nmap -f
  nmap -f -f
  nmap -ff
  ```

- **Idle (Zombie) Scan**:
  ```bash
  nmap -sI <ZOMBIE_IP> <TARGET_IP>
  ```

---

## 🧪 Service & OS Detection

- **Service Detection**:
  ```bash
  nmap -sV --version-intensity 5
  ```

- **OS Detection**:
  ```bash
  nmap -O
  ```

---

## 🌍 Traceroute

```bash
nmap --traceroute
```

---

## 🧰 Nmap Scripting Engine (NSE)

### Run Default Scripts
```bash
nmap -sC
```

### Run Specific Script
```bash
nmap --script "script-name"
```

### Script Categories

| Category    | Purpose |
|-------------|---------|
| `auth`      | Auth-related scripts |
| `broadcast` | Host discovery via broadcasts |
| `brute`     | Brute-force login testing |
| `default`   | Safe default scripts (same as `-sC`) |
| `discovery` | Extract metadata like DNS, tables |
| `dos`       | Denial-of-service detection |
| `exploit`   | Known exploits |
| `external`  | Uses third-party services |
| `fuzzer`    | Protocol fuzzing |
| `intrusive` | Brute-force or risky |
| `malware`   | Backdoor detection |
| `safe`      | Non-intrusive |
| `version`   | Version detection |
| `vuln`      | Vulnerability checks |

---

## 💾 Saving Output

| Format       | Command                 |
|--------------|-------------------------|
| Normal       | `-oN <filename>`        |
| Grepable     | `-oG <filename>`        |
| XML          | `-oX <filename>`        |
| All formats  | `-oA <filename>`        |

---

> 🧠 Tip: Always run `nmap --help` to see the latest options for your version.
