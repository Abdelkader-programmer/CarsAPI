# 🚗 واجهة برمجة تطبيقات السيارات (Cars API)

واجهة برمجة تطبيقات (API) قوية وعالية الأداء مبنية باستخدام Node.js و Express.js. توفر هذه الخدمة بيانات تفصيلية لأكثر من 400 سيارة من مختلف الماركات العالمية، مع ميزات متقدمة للبحث والفلترة وتقسيم الصفحات. تم تصميم الـ API لتكون سريعة، فعالة، وسهلة الاستخدام للمطورين.

---

## ✨ الميزات

-   **تحميل ديناميكي للبيانات:** يقوم السيرفر بقراءة وتحميل جميع ملفات `JSON` الخاصة بالسيارات تلقائيًا عند بدء التشغيل.
-   **تخزين مؤقت عالي الأداء (Caching):** يتم تخزين جميع البيانات في الذاكرة لضمان استجابة فائقة السرعة للطلبات.
-   **بحث وفلترة متقدمة:** يمكنك البحث عن السيارات بالاسم، الموديل، اللون، والسعر الأقصى.
-   **تقسيم صفحات ذكي (Smart Pagination):** للتحكم في كمية البيانات المُرجعة والحفاظ على الأداء العالي.
-   **نقاط وصول شاملة (Comprehensive Endpoints):** للحصول على كل السيارات، أو سيارات ماركة معينة، أو حتى سيارة واحدة محددة.

---

## 🚀 التثبيت والتشغيل

1.  **المتطلبات الأساسية:**
    تأكد من أن لديك [Node.js](https://nodejs.org/) مثبت على جهازك.

2.  **نسخ المشروع:**
    ```bash
    git clone <project-repository-url>
    cd <project-folder-name>
    ```

3.  **تثبيت الاعتماديات (Dependencies):**
    ```bash
    npm install express
    ```

4.  **تشغيل السيرفر:**
    ```bash
    node server.js
    ```

5.  عند التشغيل الناجح، ستظهر الرسالة التالية في وحدة التحكم (Terminal):
    ```
    The server is now running on port https://api-v1-pi.vercel.app
    ```

---

## 📚 دليل نقاط الوصول (API Endpoints Guide)

**الرابط الأساسي (Base URL):** `https://api-v1-pi.vercel.app`

### 📥 1. جلب كل السيارات
-   **Endpoint:** `GET /api/cars/all`
-   **الوصف:** يقوم بجلب قائمة بالسيارات. يدعم تقسيم الصفحات بشكل افتراضي لتحسين الأداء.
-   **Parameters:**
    -   `page` (اختياري): رقم الصفحة. الافتراضي `1`.
    -   `limit` (اختياري): عدد النتائج في الصفحة. الافتراضي `20`.
    -   `pagination` (اختياري): لتعطيل التقسيم وجلب كل السيارات، استخدم القيمة `false`.
-   **مثال (مع تقسيم الصفحات):** `https://api-v1-pi.vercel.app/api/cars/all?page=2&limit=10`
-   **مثال (بدون تقسيم الصفحات):** `https://api-v1-pi.vercel.app/api/cars/all?pagination=false`

---

### 🔍 2. البحث والفلترة المتقدمة
-   **Endpoint:** `GET /api/cars/search`
-   **الوصف:** يقوم بالبحث في جميع السيارات بناءً على معايير محددة.
-   **Parameters:**
    -   `title`: للبحث عن كلمة في اسم السيارة.
    -   `model`: للفلترة حسب سنة الموديل.
    -   `color`: للفلترة حسب اللون.
    -   `maxPrice`: للفلترة حسب السعر الأقصى.
    -   `page`, `limit`: لتقسيم صفحات نتائج البحث.
-   **مثال:** `https://api-v1-pi.vercel.app/api/cars/search?model=2024&maxPrice=80000&title=GT`

---

### 🆔 3. جلب سيارة محددة بالـ ID
    Endpoint: GET /api/cars/:brandName/:id
    الوصف: يقوم بجلب بيانات سيارة واحدة محددة عن طريق اسم الماركة (brandName) والـ ID الخاص بها.
    Parameters:
        :brandName: اسم الماركة (براند) السيارة. يجب أن يكون بأحرف صغيرة (lowercase).
        :id: المعرف الفريد (ID) للسيارة داخل الماركة.
    مثال: https://api-v1-pi.vercel.app/api/cars/bmw/1
    مثال لـ ID غير موجود: https://api-v1-pi.vercel.app/api/cars/bmw/9999

---

### 🏎️ 4. جلب السيارات حسب الماركة
-   **Endpoint:** `GET /api/cars/:brandName`
-   **الوصف:** يقوم بجلب جميع سيارات ماركة معينة. `brandName` يجب أن تكون بأحرف صغيرة.

-   **BMW**
    -   **النوع:** سيارات ألمانية رياضية وفاخرة.
    -   **الرابط:** `https://api-v1-pi.vercel.app/api/cars/bmw`

-   **Bugatti**
    -   **النوع:** سيارات فرنسية خارقة (Hypercars).
    -   **الرابط:** `https://api-v1-pi.vercel.app/api/cars/bugatti`

-   **Dodge**
    -   **النوع:** سيارات أمريكية رياضية (Muscle Cars).
    -   **الرابط:** `https://api-v1-pi.vercel.app/api/cars/dodge`

-   **Ferrari**
    -   **النوع:** سيارات إيطالية رياضية خارقة.
    -   **الرابط:** `https://api-v1-pi.vercel.app/api/cars/ferrari`

-   **Jeep**
    -   **النوع:** سيارات أمريكية للدفع الرباعي والطرق الوعرة.
    -   **الرابط:** `https://api-v1-pi.vercel.app/api/cars/jeep`

-   **Lamborghini**
    -   **النوع:** سيارات إيطالية رياضية خارقة.
    -   **الرابط:** `https://api-v1-pi.vercel.app/api/cars/lamborghini`

-   **Mercedes**
    -   **النوع:** سيارات ألمانية فاخرة وراقية.
    -   **الرابط:** `https://api-v1-pi.vercel.app/api/cars/mercedes`

-   **Peugeot**
    -   **النوع:** سيارات فرنسية أنيقة.
    -   **الرابط:** `https://api-v1-pi.vercel.app/api/cars/peugeot`

-   **Porsche**
    -   **النوع:** سيارات رياضية ألمانية فاخرة.
    -   **الرابط:** `https://api-v1-pi.vercel.app/api/cars/porsche`

-   **Tesla**
    -   **النوع:** سيارات أمريكية كهربائية رائدة.
    -   **الرابط:** `https://api-v1-pi.vercel.app/api/cars/tesla`
