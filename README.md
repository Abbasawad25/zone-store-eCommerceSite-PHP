# RixZone Store 🛒
### نظام متجر إلكتروني متكامل | Complete E-Commerce System

![PHP](https://img.shields.io/badge/PHP-5.6%20%7C%207.4-777BB4?logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-SQL-4479A1?logo=mysql&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-UI-7952B3?logo=bootstrap&logoColor=white)
![Version](https://img.shields.io/badge/branch-v1-blue)

**🌐 Live Demo / معاينة مباشرة:** https://zonestores.kesug.com

> **Recommended PHP Version / نسخة PHP الموصى بها:** `5.6` or `7.4`

---

## 📑 Table of Contents / المحتويات

1. [Features / المميزات](#-features--المميزات)
2. [Requirements / المتطلبات](#-requirements--المتطلبات)
3. [Installation / طريقة التثبيت](#-installation--طريقة-التثبيت)
4. [Admin Login / الدخول للوحة التحكم](#-admin-login--للدخول-الي-لوحة-التحكم)
5. [Security Tips / نصائح الأمان](#-security-tips--نصائح-الأمان)
6. [Troubleshooting / حل المشاكل](#-troubleshooting--حل-المشاكل)
7. [FAQ / أسئلة شائعة](#-faq--أسئلة-شائعة)
8. [Developers / المطورون](#-developed-by)
9. [Support / الدعم](#-support--للمساعدة-والدعم)

---

## ✨ Features / المميزات

- 🛍️ Full online store: products, categories, cart, checkout, and orders
  متجر إلكتروني كامل: منتجات، تصنيفات، سلة، دفع، وطلبات
- 🎛️ Admin dashboard to manage the whole store
  لوحة تحكم لإدارة المتجر بالكامل
- 💳 Multiple payment methods (PayPal, Bank Transfer)
  طرق دفع متعددة (PayPal، حوالة بنكية)
- 🚚 Delivery system with custom areas and prices
  نظام توصيل بمناطق وأسعار قابلة للتعديل
- 📧 SMTP email notifications
  إشعارات بريد إلكتروني عبر SMTP
- 💬 Live chat with Tawk.to
  دردشة مباشرة مع العملاء عبر Tawk.to
- 🌍 Bilingual-friendly (Arabic / English)
  يدعم العربية والإنجليزية
- 📱 Responsive design built with Bootstrap
  تصميم متجاوب مع جميع الشاشات

---

## 📋 Requirements / المتطلبات

| Requirement | Details |
|---|---|
| PHP | 5.6 or 7.4 (recommended) |
| Database | MySQL / MariaDB |
| Web Server | Apache (XAMPP / WAMP / cPanel / InfinityFree) |
| Tools | phpMyAdmin |

---

## 🚀 Installation / طريقة التثبيت

### 1. Database Setup / إعداد قاعدة البيانات

- Create a database named `ecommerceweb` in phpMyAdmin
  أنشئ قاعدة بيانات باسم `ecommerceweb` في phpMyAdmin
- Import the file `zone.sql`
  استورد الملف `zone.sql`

### 2. Database Connection / الاتصال بقاعدة البيانات

> ⚠️ You must complete this step for the site to work.
> يجب عليك إكمال إعداد الاتصال بقاعدة البيانات.

Go to / اذهب إلى: `admin/inc/config.php`

(ادخل فولدر `admin` وبعدها فولدر `inc` وبعدها ملف `config.php` وعدّل:)

```php
<?php
// Database Host
$dbhost = 'localhost';

// Database Name
$dbname = 'ecommerceweb';

// Database Username
$dbuser = 'root';

// Database Password
$dbpass = '';

// Defining base url
define("BASE_URL", "http://localhost/rixzone/");

// Getting Admin url
define("ADMIN_URL", BASE_URL . "admin" . "/");
?>
```

📝 **On a live server / على السيرفر الحقيقي:** change `BASE_URL` to your domain, for example:

```php
define("BASE_URL", "https://zonestores.kesug.com/");
```

### 3. Payment Methods / طرق الدفع

The system supports multiple payment methods.
النظام يدعم طرق دفع متعددة.

**PayPal Setup:**
Go to `Admin > Payment Settings`

```php
// Add your PayPal account
$paypal_email     = "your-paypal@email.com";
$paypal_client_id = "YOUR_CLIENT_ID";
$paypal_secret    = "YOUR_SECRET";
```

**Bank Transfer / حوالة بنكية:**

```php
$bank_name      = "Bank of Khartoum"; // قم بإضافة اسم البنك
$account_name   = "Abbas Awad";       // اسم صاحب الحساب
$account_number = "123456789";        // قم بإضافة رقم الحساب
$iban           = "SD123456789";      // IBAN
```

### 4. SMTP Email Service / خدمة البريد الإلكتروني

Go to `Admin > Email Settings`

```text
SMTP Host:     smtp.gmail.com
SMTP Port:     587
SMTP Username: your-email@gmail.com
SMTP Password: your-app-password
From Email:    your-email@gmail.com
```

💡 **Gmail tip:** use an **App Password** (needs 2-Step Verification enabled), not your normal Gmail password.
نصيحة: استخدم "App Password" من إعدادات حساب جوجل وليس كلمة السر العادية.

### 5. Delivery System / نظام التوصيل

The system supports delivery and delivery services, so orders can be shipped to customers.
النظام يدعم ميزة التوصيل وخدمات التوصيل بحيث يمكن إرسال الطلب للعميل.

Add delivery areas from `Admin > Shipping Settings`:

```php
$delivery_area  = "Khartoum";
$delivery_price = "5000 SDG";
```

### 6. Live Chat / خدمة الدردشة المباشرة

Create an account on [Tawk.to](https://www.tawk.to) and add your code in `Admin > General Settings`:
أنشئ حساب في Tawk.to وضع الكود في `Admin > General Settings`:

```html
<!-- Live Chat Code -->
<script type="text/javascript">
var Tawk_API=Tawk_API||{}, Tawk_LoadStart=new Date();
(function(){
var s1=document.createElement("script"),s0=document.getElementsByTagName("script")[0];
s1.async=true;
s1.src='https://embed.tawk.to/YOUR_ID/default';
s1.charset='UTF-8';
s1.setAttribute('crossorigin','*');
s0.parentNode.insertBefore(s1,s0);
})();
</script>
```

---

## 🔐 Admin Login / للدخول إلى لوحة التحكم

Open / افتح:

- Live: `https://zonestores.kesug.com/admin/login.php`
- Local: `http://localhost/rixzone/admin/login.php`

**Default Admin Login Details:**

```text
Email    : admin@mail.com
Password : Password@123
```

> 🚨 **IMPORTANT:** Change the default email and password immediately after your first login!
> **مهم جداً:** غيّر الإيميل وكلمة السر الافتراضية فور أول دخول!

---

## 🛡️ Security Tips / نصائح الأمان

Before going live / قبل نشر الموقع:

- ✅ Change the default admin password / غيّر كلمة سر الأدمن الافتراضية
- ✅ Use a strong database password (not empty) on the live server / استخدم باسورد قوي لقاعدة البيانات
- ✅ Never upload real API keys, PayPal secrets, or SMTP passwords to a public GitHub repo / لا ترفع مفاتيح أو كلمات سر حقيقية على GitHub العام
- ✅ Delete or protect `zone.sql` from public access after importing / احذف أو احمِ ملف `zone.sql` بعد الاستيراد
- ✅ Enable HTTPS (SSL) / فعّل شهادة SSL
- ✅ Take regular database backups / خذ نسخة احتياطية من قاعدة البيانات بانتظام
- ✅ Keep PHP and your hosting up to date / حدّث PHP والاستضافة

---

## 🧰 Troubleshooting / حل المشاكل

| Problem / المشكلة | Solution / الحل |
|---|---|
| Blank page or DB error / صفحة بيضاء أو خطأ قاعدة بيانات | Check `admin/inc/config.php` (host, name, user, password) |
| Images/CSS not loading / الصور أو التنسيق لا يظهر | Check `BASE_URL` — it must end with `/` and match your real URL |
| Can't log in to admin / لا يمكن دخول الأدمن | Make sure `zone.sql` was imported correctly |
| Emails not sending / الإيميلات لا تُرسل | Verify SMTP settings and use a Gmail App Password |
| PHP errors on a new version / أخطاء PHP | Switch the server to PHP 5.6 or 7.4 |
| Site works locally but not online / يعمل محلياً ولا يعمل أونلاين | Update `BASE_URL` and the DB credentials for your host |

---

## ❓ FAQ / أسئلة شائعة

**Can I use it on free hosting? / هل يعمل على استضافة مجانية؟**
Yes, the demo runs on a free host. Just make sure PHP 5.6/7.4 and MySQL are available.
نعم، المعاينة تعمل على استضافة مجانية، فقط تأكد من توفر PHP و MySQL.

**Can I add another payment method or language? / هل يمكن إضافة طريقة دفع أو لغة؟**
Yes, contact us (see Support below). / نعم، تواصل معنا.

**Can I change the design? / هل يمكن تغيير التصميم؟**
Yes, the project uses Bootstrap, HTML and CSS, so it's easy to customize.
نعم، المشروع مبني على Bootstrap وسهل التعديل.

---

## 👨‍💻 Developed by

- **Abbas Awad**
- **Hammad Hassan**

**Technologies:** PHP / SQL / Bootstrap / HTML / CSS / JS

---

## 📞 Support / للمساعدة والدعم

For help, if you face a problem, or you want add-ons for the project, payment methods, languages, or a paid version, contact us.
لو واجهتك مشكلة أو تريد إضافات للمشروع أو طرق دفع أو لغة أو طلب نسخة مدفوعة، اتصل بنا.

- 📧 Email: aliexsandstone@gmail.com
- 💬 WhatsApp: +249124302466
- 📘 Facebook: https://facebook.com/abbasawad26

---

## 👀 Preview / معاينة المشروع

🔗 https://zonestores.kesug.com

---

## 📤 Upload to GitHub / رفع المشروع

```bash
cd C:\xampp\htdocs\rixzone
git add README.md
git commit -m "Final README all in one"
git push -u origin v1
```

---

© 2026 RixZone Store — All rights reserved / جميع الحقوق محفوظة
