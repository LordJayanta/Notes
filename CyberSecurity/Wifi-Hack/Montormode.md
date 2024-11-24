# Normal Mode > Monitor mode

Tumhar laptop er **Wi-Fi adapter** monitor mode support kore kina seta check korar jonno **Linux tools** er help nite hobe. Kali Linux install korar por ei process-ta follow koro:

---

### **Step 1: Wi-Fi Adapter Er Name Check Koro**
Linux terminal e command run koro:
```bash
iwconfig
```
Ei command tumhar system er Wi-Fi interface gular list dibe. Default Wi-Fi adapter er naam hote pare `wlan0`, `wlan1`, etc.

---

### **Step 2: Monitor Mode Enable Korar Try Koro**
Monitor mode enable korar jonno ei command run koro:
```bash
sudo airmon-ng start wlan0
```

- **`wlan0`**: Ei naam tumhar Wi-Fi adapter er naam ke represent kore. Jodi adapter er naam `wlan1` hoy, seta use korte hobe.

- Jodi monitor mode successfully enable hoy, terminal e message dibe:
  ```
  monitor mode enabled on wlan0mon
  ```
  Ekhane `wlan0mon` holo monitor mode e Wi-Fi interface er naam.

#### Jodi kono error show kore, tahole Wi-Fi adapter monitor mode support kore na.

---

### **Step 3: Monitor Mode Er Functional Test**
Monitor mode successful enable korar por nearby Wi-Fi networks scan korte try koro:
```bash
sudo airodump-ng wlan0mon
```

- Jodi nearby networks detect hoy, tahole tumhar Wi-Fi adapter monitor mode support kore.
- Jodi kono network detect na hoy, tahole support problem hote pare, ba drivers thik thak moto configured na hote pare.

---

### **Step 4: Driver Compatibility Check**
Jodi monitor mode enable na hoy, tahole Wi-Fi adapter er compatibility check korte hobe:
1. **Check Adapter Model**: Tumhar Wi-Fi adapter er model janar jonno command run koro:
   ```bash
   lspci | grep -i wireless
   ```
   Athoba:
   ```bash
   lsusb
   ```
   Ei command adapter er exact model name show korbe.

2. **Adapter Compatibility Search Koro**:
   - [Aircrack-ng Compatible Devices List](https://www.aircrack-ng.org/doku.php?id=compatibility_drivers): Ei website theke adapter er model match koro monitor mode support check korar jonno.

---

### **Step 5: Windows E Adapter Compatibility Check**
Windows OS theke monitor mode compatibility janar jonno ei steps follow koro:

1. **Command Prompt (cmd)** Open Koro:
   Command prompt e ei command run koro:
   ```bash
   netsh wlan show drivers
   ```
2. Output e search koro:
   ```
   Hosted network supported : Yes
   ```
   - Jodi output e "Monitor mode" support er mention thake, tahole Windows eo limited monitor mode support thakte pare.

---

### **Recommendation**
1. Jodi tumhar default Wi-Fi adapter monitor mode support na kore, external Wi-Fi adapter use korte hobe. **ALFA AWUS036NHA** ar **TP-Link TL-WN722N (V1)** common options.
2. Jodi monitor mode enable korte na paro, Wi-Fi adapter er driver update koro Kali Linux e:
   ```bash
   sudo apt update
   sudo apt install firmware-linux
   ```

---

<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

# Monitor Mode > Normal mode

**Monitor mode theke Wi-Fi adapter ke normal managed mode e pheranor jonno**, tumi niche diye deya steps follow korte paro:

---

### **Step 1: Monitor Mode Disable Koro**

Terminal e command run koro:
```bash
sudo airmon-ng stop wlan0mon
```
- **`wlan0mon`**: Monitor mode e thaka Wi-Fi adapter er naam (jodi eta `wlan0mon` na hoy, tahole correct naam use koro jeita `airmon-ng start` command er por show kore).

Ei command tumhar Wi-Fi adapter ke monitor mode theke normal managed mode e niye jabe.

---

### **Step 2: Wi-Fi Interface Ke Restart Koro**

Adapter ke restart korte ei command run koro:
```bash
sudo service NetworkManager restart
```
Eta tumhar Wi-Fi interface ke abar re-enable kore.

---

### **Step 3: Verify Managed Mode**
Wi-Fi adapter managed mode e ache kina verify korte ei command use koro:
```bash
iwconfig
```

Output e Wi-Fi adapter er status show korbe:
- **Mode: Managed** hole bujhte parbe je adapter normal Wi-Fi mode e phire esheche.

---

### **Step 4: Jodi Wi-Fi Connect Na Hoy**
Jodi Wi-Fi network e connect korte problem hoy, tahole ei command-gula use koro:

1. **Wi-Fi Interface Down Koro**:
   ```bash
   sudo ifconfig wlan0 down
   ```

2. **Normal Mode E Set Koro**:
   ```bash
   sudo iwconfig wlan0 mode managed
   ```

3. **Wi-Fi Interface Up Koro**:
   ```bash
   sudo ifconfig wlan0 up
   ```

---

Eivabe tumhar adapter ke monitor mode theke normal managed mode e niye eshe Wi-Fi network e connect korte parbe. 