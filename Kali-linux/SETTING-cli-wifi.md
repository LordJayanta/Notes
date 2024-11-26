আপনার Kali Linux টার্মিনাল মোডে যদি Wi-Fi সংযোগ চেক করতে চান এবং সংযোগ স্থাপন করতে চান, তবে নিচের ধাপগুলো অনুসরণ করুন:

---

### ধাপ ১: Wi-Fi সংযোগ চেক করুন
আপনার ল্যাপটপ Wi-Fi এর সাথে সংযুক্ত কিনা তা চেক করতে:
1. নিচের কমান্ডটি চালান:
   ```bash
   nmcli device status
   ```
   এটি একটি তালিকা দেখাবে যেখানে আপনার ডিভাইসের নাম, টাইপ (যেমন Wi-Fi), এবং অবস্থা (`connected` বা `disconnected`) উল্লেখ থাকবে।

   **উদাহরণ আউটপুট:**
   ```
   DEVICE     TYPE      STATE         CONNECTION
   wlan0      wifi      connected     Your-WiFi-Network-Name
   eth0       ethernet  unavailable   --
   lo         loopback  unmanaged     --
   ```
   যদি **`STATE`** `connected` দেখায়, তাহলে আপনি Wi-Fi এর সাথে সংযুক্ত আছেন।

---

### ধাপ ২: Wi-Fi সংযোগ স্থাপন করুন (যদি সংযুক্ত না থাকেন)
Wi-Fi নেটওয়ার্কের সাথে সংযোগ করতে নিচের ধাপগুলো অনুসরণ করুন:

#### পদ্ধতি ১: `nmtui` ব্যবহার করে
1. **`nmtui`** চালান:
   ```bash
   sudo nmtui
   ```
2. একটি টেক্সট-ভিত্তিক ইন্টারফেস খুলবে। এখানে:
   - **"Activate a connection"** অপশনটি সিলেক্ট করুন।
   - আপনার Wi-Fi নেটওয়ার্ক তালিকা থেকে সিলেক্ট করুন এবং পাসওয়ার্ড প্রদান করুন।
3. সংযোগ সফল হলে **"Quit"** নির্বাচন করুন।

#### পদ্ধতি ২: `nmcli` ব্যবহার করে
1. উপলব্ধ Wi-Fi নেটওয়ার্কের তালিকা দেখতে:
   ```bash
   nmcli device wifi list
   ```
   **উদাহরণ আউটপুট:**
   ```
   SSID            MODE   CHAN  RATE       SIGNAL  BARS  SECURITY
   Your-Network    Infra  6     54 Mbit/s  70      ▂▄▆_  WPA2
   ```

2. নেটওয়ার্কে সংযোগ করতে:
   ```bash
   nmcli device wifi connect "Your-Network" password "Your-Password"
   ```
   **Replace** `"Your-Network"` এবং `"Your-Password"` আপনার Wi-Fi নেটওয়ার্কের নাম এবং পাসওয়ার্ড দিয়ে।

3. সংযোগ সফল হলে আপনি এই মেসেজ দেখতে পাবেন:
   ```
   Device 'wlan0' successfully activated with 'network-uuid'
   ```

---

### ধাপ ৩: সংযোগ যাচাই করুন
1. Wi-Fi সংযোগ নিশ্চিত করতে:
   ```bash
   nmcli device show wlan0
   ```
   অথবা:
   ```bash
   ping google.com
   ```
   যদি **ping** কাজ করে, তাহলে আপনার Wi-Fi সংযোগ সক্রিয়।

---

### অতিরিক্ত: সমস্যার সমাধান
1. যদি Wi-Fi ডিভাইস কাজ না করে, তাহলে চেক করুন ডিভাইসটি সঠিকভাবে ডিটেক্ট হচ্ছে কি না:
   ```bash
   lspci | grep -i wireless
   ```
   অথবা:
   ```bash
   lsusb
   ```
2. Wi-Fi ড্রাইভার ইনস্টল করতে:
   ```bash
   sudo apt install firmware-iwlwifi
   sudo modprobe -r iwlwifi && sudo modprobe iwlwifi
   ```

যদি সমস্যা থাকে বা সংযোগে বাধা পান, জানাতে দ্বিধা করবেন না। 😊