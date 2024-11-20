Tumi jodi Linux system e Metasploit Framework install korte chao, tahole ei step-by-step process ta follow koro:

---

### **Step 1: System Update**
Pothome system ta update kore nao, jeno sob latest packages available thake. Terminal e ei command execute koro:

```bash
sudo apt update && sudo apt upgrade -y
```

---

### **Step 2: Install Required Dependencies**
Metasploit er jonno kichu dependencies lage. Ei command gulo diye install koro:

```bash
sudo apt install wget curl git -y
```

---

### **Step 3: Download Metasploit Installer**
Metasploit Framework er official script download koro:

```bash
curl https://raw.githubusercontent.com/rapid7/metasploit-framework/master/msfinstall > msfinstall
```

---

### **Step 4: Set Permissions and Run Installer**
Script ta executable koro and tarpor execute koro:

```bash
chmod +x msfinstall
sudo ./msfinstall
```

---

### **Step 5: Verify Installation**
Install complete hole, `msfconsole` command execute kore verify koro:

```bash
msfconsole
```

Jodi console open hoy, tahole installation successful.

---

### **Step 6: Troubleshooting (Optional)**
Jodi kono error hoy, check koro:
- `ruby` ba `bundler` install ache kina:
  ```bash
  sudo apt install ruby-full -y
  gem install bundler
  ```

---

### **Additional Notes**
- Kali Linux install korle Metasploit Framework pre-installed thake.
- Jodi portable version er dorkar hoy, tahole Docker er madhome use korte paro:
  ```bash
  sudo docker run -it --rm metasploitframework/metasploit-framework
  ```

