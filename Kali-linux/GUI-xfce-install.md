আপনার দেওয়া কমান্ডগুলি **GUI ইন্টারফেস**-এর জন্য প্রয়োজনীয় লাইব্রেরি এবং প্যাকেজ সরিয়ে দিয়েছে, যার কারণে আপনার **Kali Linux** এখন শুধুমাত্র টার্মিনাল মোডে বুট হচ্ছে। এটি ঠিক করার জন্য আপনাকে GUI ডেস্কটপ এনভায়রনমেন্ট পুনরায় ইনস্টল করতে হবে এবং সঠিকভাবে সেটআপ করতে হবে। নিচে ধাপে ধাপে সমাধান দেওয়া হলো:

---

### ধাপ ১: সিস্টেম আপডেট করুন
1. সিস্টেমে লগইন করুন এবং নিচের কমান্ডটি চালান:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
   এটি নিশ্চিত করবে যে আপনার প্যাকেজ ম্যানেজার সঠিকভাবে কাজ করছে।

---

### ধাপ ২: GUI ডেক্সটপ এনভায়রনমেন্ট পুনরায় ইনস্টল করুন
#### GNOME (Kali Linux-এর ডিফল্ট GUI) পুনরায় ইনস্টল করতে:
1. নিচের কমান্ডটি দিন:
   ```bash
   sudo apt install kali-desktop-gnome -y
   ```
2. ইনস্টলেশন শেষ হলে GUI ডেক্সটপ এনভায়রনমেন্ট আবার প্রস্তুত হবে।

#### Xfce (লাইটওয়েট GUI) ইনস্টল করতে:
1. যদি GNOME পছন্দ না করেন বা কম রিসোর্স ব্যবহার করতে চান, Xfce ইনস্টল করতে এই কমান্ডটি দিন:
   ```bash
   sudo apt install kali-desktop-xfce -y
   ```

---

### ধাপ ৩: Display Manager পুনরায় ইনস্টল করুন
GUI চালাতে **Display Manager** প্রয়োজন। LightDM বা GDM সাধারণত ব্যবহৃত হয়।

1. LightDM ইনস্টল করতে:
   ```bash
   sudo apt install lightdm -y
   ```
2. ইনস্টল করার সময় **LightDM** কে ডিফল্ট Display Manager হিসাবে নির্বাচন করুন।

---

### ধাপ ৪: GUI চালু করুন
1. নিচের কমান্ড দিয়ে GUI চালানোর চেষ্টা করুন:
   ```bash
   sudo systemctl start gdm
   ```
   অথবা
   ```bash
   sudo systemctl start lightdm
   ```

2. যদি কাজ করে, তাহলে GUI-তে ফিরে আসবেন। যদি না হয়, তাহলে রিস্টার্ট করার পর স্বয়ংক্রিয়ভাবে GUI চালু করতে নিচের কমান্ড দিন:
   ```bash
   sudo systemctl set-default graphical.target
   ```

---

### ধাপ ৫: নেটওয়ার্ক সংযোগ চেক করুন
আপনার Wi-Fi বা ইন্টারনেট সংযোগ কাজ করছে কিনা তা চেক করতে:
1. ইন্টারনেট সংযোগ চেক করুন:
   ```bash
   ping google.com
   ```
2. যদি Wi-Fi কানেকশন না থাকে, তবে **nmtui** ব্যবহার করে নেটওয়ার্ক সংযোগ স্থাপন করুন:
   ```bash
   sudo nmtui
   ```
   এখানে **"Activate a connection"** অপশনে যান এবং আপনার Wi-Fi নেটওয়ার্ক নির্বাচন করুন।

---

### ধাপ ৬: রিস্টার্ট করুন
1. সিস্টেম রিস্টার্ট করুন:
   ```bash
   sudo reboot
   ```

---

### ধাপ ৭: সমস্যা হলে লগ চেক করুন
যদি এখনও GUI চালু না হয়, লগ ফাইল চেক করে সমস্যার কারণ খুঁজে বের করুন:
   ```bash
   cat /var/log/Xorg.0.log
   ```
এই ফাইলটি দেখাবে কেন GUI সঠিকভাবে লোড হচ্ছে না।

---

যদি সমস্যাটি সমাধান না হয় বা আপনি কোনো নির্দিষ্ট ধাপে আটকে যান, জানাবেন। আমি আরও সাহায্য করব। 😊