WiFi network e kon kon device connected ache seta `nmap` diye check korar jonno niche step-gulo follow korun:

---

### **1. Network er Subnet Address Ber Kora**
Prothome apnar WiFi network er subnet range ber korte hobe. Terminal e command likhun:

```bash
ip a
```
Athoba:

```bash
ifconfig
```

Ekhan theke apnar local IP address (e.g., `192.168.1.5`) o subnet mask ber korun.

#### Example:
Apnar IP jodi hoy `192.168.1.5` ebong subnet mask hoy `255.255.255.0`, tahole apnar subnet range hobe `192.168.1.0/24`.

---

### **2. nmap Install Kora**
Jodi apnar system e `nmap` install na thake, tahole install korun:

- **Ubuntu/Debian**:
  ```bash
  sudo apt update && sudo apt install nmap -y
  ```

- **Fedora/Red Hat**:
  ```bash
  sudo dnf install nmap -y
  ```

- **Arch Linux**:
  ```bash
  sudo pacman -S nmap
  ```

---

### **3. Network Scan Chalan**
Niche command chalale connected device-gulo dekha jabe:

```bash
nmap -sn 192.168.1.0/24
```

#### Explanation:
- `-sn` flag mane ping scan (device discovery), port scan kora hobe na.
- `192.168.1.0/24` apnar network range ke define kore.

---

### **4. Result Analysis**
Scan complete hole apni connected device-gulo dekhte paben:

```plaintext
Nmap scan report for 192.168.1.1
Host is up (0.0050s latency).
MAC Address: XX:XX:XX:XX:XX:XX (Router Manufacturer)

Nmap scan report for 192.168.1.101
Host is up (0.0020s latency).
MAC Address: XX:XX:XX:XX:XX:XX (Device Manufacturer)
```

**Router** er IP address (usually `192.168.1.1`) er shathe connected onno device er IP o MAC address list paben.

---

### **5. Advanced Scan (Optional)**
Device er port o service information scan korte chaile:

```bash
nmap -A 192.168.1.0/24
```

---

Ei vabe apni apnar WiFi network e connected shob device ber korte parben. Jodi kono specific question thake, janate paren! 😊