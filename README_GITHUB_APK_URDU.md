# 🌿 گلزار (GULZAR) — گٹ ہب سٹینڈ الون ایپ اور APK بلڈ گائیڈ

اس پیکج میں آپ کی **گلزار (Gulzar Smart Home Garden)** ایپ کا مکمل اپڈیٹ شدہ اور بگز سے پاک ورژن موجود ہے، جس میں اسٹوریج، ڈپلیکیٹ پودوں/فوٹوز، اور انسائیکلوپیڈیا کے تمام مسائل حل کر دیے گئے ہیں۔

---

## 📦 اس زپ پیکج میں شامل فائلیں:

1. **`index.html`** — مکمل اپڈیٹ شدہ گلزار ایپ (IndexedDB ریس کنڈیشن فکس، 50% کم ڈیٹا بیس سائز، ڈپلیکیٹ فکس، اور GitHub Single-File Database Sync کے ساتھ)۔
2. **`manifest.json`** — سٹینڈ الون انسٹالیشن اور فل اسکرین موبائل موڈ کی کنفیگریشن۔
3. **`sw.js`** — آف لائن سروس ورکر (Service Worker) تاکہ گٹ ہب پیجز یا موبائل پر بغیر انٹرنیٹ کے بھی ایپ فوری کھلے۔
4. **`icon-192.png` & `icon-512.png`** — گلزار کے ہائی ریزولوشن ایپ آئیکنز۔
5. **`capacitor.config.json` & `package.json`** — ایپ کو Capacitor کے ذریعے نیٹو اینڈرائیڈ ایپ بنانے کی فائلیں۔
6. **`.github/workflows/build-apk.yml`** — گٹ ہب ایکشنز (GitHub Actions) کی آٹومیٹک فائل جو گٹ ہب کے سرور پر خودکار طور پر آپ کے لیے **`.apk`** فائل تیار کر دیتی ہے!

---

## 🚀 طریقہ 1: گٹ ہب (GitHub) سے خودکار `.apk` اور سٹینڈ الون ایپ بنانے کا طریقہ

1. اپنے GitHub اکاؤنٹ پر ایک نئی Repository بنائیں (مثلاً `gulzar-garden`)۔
2. اس زپ فائل کی تمام فائلیں (`index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`, `package.json`, `capacitor.config.json` اور فولڈر `.github/workflows/build-apk.yml`) اپنی ریپوزٹری میں اپلوڈ (Commit) کر دیں۔
3. **لائیو ایپ لنک (GitHub Pages):**
   - اپنی ریپوزٹری کے **Settings → Pages** میں جائیں۔
   - **Branch** میں `main` چن کر **Save** دبائیں۔
   - آپ کا مستقل لنک تیار ہو جائے گا۔ فون کے Chrome میں کھول کر **Add to Home Screen / Install App** کریں۔
4. **مکمل `.apk` فائل ڈاؤن لوڈ کرنا (GitHub Actions):**
   - اپنی ریپوزٹری کے اوپر **Actions** ٹیب پر کلک کریں۔
   - وہاں **Build Gulzar Standalone Android APK** ورک فلو چلتا نظر آئے گا۔
   - چند منٹ بعد جب اس پر سبز ٹک (✅) آ جائے، تو اس پر کلک کر کے نیچے **Artifacts** سیکشن سے **`Gulzar-Standalone-Android-APK`** زپ ڈاؤن لوڈ کریں — اس کے اندر آپ کی تیار شدہ `.apk` فائل موجود ہوگی!

---

## 🐙 طریقہ 2: گٹ ہب کی ایک ہی ڈیٹا بیس فائل (`gulzar-database.json`) میں آٹو سیو اور ریسٹور

آپ نے بالکل درست سوچا تھا کہ بار بار الگ فائلیں ڈاؤن لوڈ کرنے کے بجائے ایک ہی ڈیٹا بیس میں ڈیٹا محفوظ ہونا چاہیے:
1. اپنے GitHub اکاؤنٹ میں **Settings → Developer settings → Personal access tokens → Tokens (classic)** میں جائیں۔
2. **Generate new token** پر کلک کریں، اس میں صرف **`gist`** والے باکس پر ٹک لگائیں اور ٹوکن کاپی کر لیں۔
3. گلزار ایپ کی **Settings (⚙️) → Extra Restore Points → Live Cloud Sync** میں جائیں۔
4. وہاں نیا سیکشن **🐙 GitHub Single-File Database Sync** موجود ہے:
   - اپنا **GitHub Token** پیسٹ کریں۔
   - پہلی بار **Gist ID** کو خالی چھوڑ کر **`🐙 Save to 1 GitHub DB`** دبائیں۔
   - ایپ خودکار طور پر آپ کے گٹ ہب پر ایک پرائیویٹ `gulzar-database.json` بنا دے گی اور اس کا Gist ID محفوظ کر لے گی۔
   - اس کے بعد جب بھی آپ **`Save to 1 GitHub DB`** یا **`Restore from GitHub DB`** دبائیں گے، ہمیشہ اسی ایک فائل میں ڈیٹا اپڈیٹ اور ریسٹور ہوگا!
