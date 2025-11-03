# تصميم واجهات برمجة التطبيقات (API Design) لمنصة السوق البيطرية

## 1. مقدمة

تهدف هذه الوثيقة إلى تقديم تصميم شامل لواجهات برمجة التطبيقات (APIs) لمنصة السوق البيطرية. تم تصميم هذه الواجهات بناءً على مبادئ RESTful لضمان تواصل فعال وآمن بين الواجهة الأمامية (Angular) والواجهة الخلفية (.NET Core). يركز التصميم على الوضوح، قابلية التوسع، والأمان.

### المبادئ الأساسية:

- **RESTful:** سيتم استخدام أفعال HTTP (GET, POST, PUT, DELETE) مع موارد واضحة (Nouns).
- **Stateless:** كل طلب من العميل إلى الخادم يجب أن يحتوي على جميع المعلومات اللازمة لفهم الطلب وتنفيذه.
- **JSON:** سيتم استخدام تنسيق JSON لجميع عمليات تبادل البيانات.
- **التوثيق (Documentation):** سيتم استخدام **Swagger (OpenAPI)** لتوثيق جميع الـ APIs بشكل تلقائي، مما يوفر واجهة تفاعلية للمطورين لاختبار وفهم الـ Endpoints.
- **الأمان (Security):** سيتم استخدام **JWT (JSON Web Tokens)** للمصادقة (Authentication) وتحديد صلاحيات الوصول (Authorization) لكل طلب.
- **التحقق من الصحة (Validation):** سيتم التحقق من صحة جميع البيانات المدخلة في الـ Backend لضمان تكامل البيانات.
- **معالجة الأخطاء (Error Handling):** سيتم توفير رسائل خطأ واضحة وموحدة بتنسيق JSON قياسي.

## 2. المصادقة والترخيص (Authentication & Authorization)

1.  **تسجيل الدخول (Login):** يرسل المستخدم البريد الإلكتروني وكلمة المرور إلى `POST /api/auth/login`.
2.  **الحصول على Token:** في حال نجاح المصادقة، يقوم الخادم بإرجاع JWT Access Token و Refresh Token.
3.  **الوصول إلى الموارد المحمية:** يتم إرسال الـ Access Token في ترويسة كل طلب (`Authorization: Bearer <token>`).
4.  **صلاحيات الوصول:** يتم تحديد صلاحيات الوصول لكل Endpoint بناءً على دور المستخدم (Buyer, Seller, Admin) الموجود داخل الـ Token.

## 3. تصميم نقاط النهاية (API Endpoints)

**Base URL:** `/api`

### 3.1. المصادقة (Authentication)

| Method | Endpoint | Description | Authorization |
| :--- | :--- | :--- | :--- |
| `POST` | `/auth/register` | تسجيل حساب جديد (مشتري أو بائع) | Public |
| `POST` | `/auth/login` | تسجيل الدخول والحصول على JWT | Public |
| `POST` | `/auth/refresh-token` | تحديث الـ Access Token باستخدام Refresh Token | Authenticated |

### 3.2. المنتجات (Products)

| Method | Endpoint | Description | Authorization |
| :--- | :--- | :--- | :--- |
| `GET` | `/products` | الحصول على قائمة بالمنتجات مع دعم التصفية والترتيب والترقيم | Public |
| `GET` | `/products/{id}` | الحصول على تفاصيل منتج معين | Public |
| `POST` | `/products` | إضافة منتج جديد (للبائعين فقط) | Seller |
| `PUT` | `/products/{id}` | تعديل منتج موجود | Seller |
| `DELETE` | `/products/{id}` | حذف منتج | Seller, Admin |

### 3.3. الفئات والعلامات التجارية (Categories & Brands)

| Method | Endpoint | Description | Authorization |
| :--- | :--- | :--- | :--- |
| `GET` | `/categories` | الحصول على قائمة بجميع الفئات | Public |
| `GET` | `/brands` | الحصول على قائمة بجميع العلامات التجارية | Public |
| `POST` | `/categories` | إضافة فئة جديدة | Admin |
| `PUT` | `/categories/{id}` | تعديل فئة موجودة | Admin |

### 3.4. عربة التسوق (Shopping Cart)

| Method | Endpoint | Description | Authorization |
| :--- | :--- | :--- | :--- |
| `GET` | `/cart` | الحصول على محتويات عربة التسوق للمستخدم الحالي | Buyer |
| `POST` | `/cart/items` | إضافة منتج إلى عربة التسوق | Buyer |
| `PUT` | `/cart/items/{itemId}` | تعديل كمية منتج في عربة التسوق | Buyer |
| `DELETE` | `/cart/items/{itemId}` | حذف منتج من عربة التسوق | Buyer |

### 3.5. الطلبات (Orders)

| Method | Endpoint | Description | Authorization |
| :--- | :--- | :--- | :--- |
| `POST` | `/orders` | إنشاء طلب جديد من عربة التسوق | Buyer |
| `GET` | `/orders` | الحصول على قائمة بطلبات المستخدم الحالي (للمشتري) أو الطلبات الواردة (للبائع) | Buyer, Seller |
| `GET` | `/orders/{id}` | الحصول على تفاصيل طلب معين | Buyer, Seller, Admin |
| `PUT` | `/orders/{id}/status` | تحديث حالة الطلب (مثل "تم الشحن") | Seller, Admin |

### 3.6. المستخدمون والملف الشخصي (Users & Profile)

| Method | Endpoint | Description | Authorization |
| :--- | :--- | :--- | :--- |
| `GET` | `/profile` | الحصول على الملف الشخصي للمستخدم الحالي | Authenticated |
| `PUT` | `/profile` | تعديل الملف الشخصي للمستخدم الحالي | Authenticated |
| `GET` | `/profile/addresses` | الحصول على عناوين الشحن للمستخدم الحالي | Buyer |
| `POST` | `/profile/addresses` | إضافة عنوان شحن جديد | Buyer |

### 3.7. لوحة تحكم المسؤول (Admin Panel)

| Method | Endpoint | Description | Authorization |
| :--- | :--- | :--- | :--- |
| `GET` | `/admin/users` | الحصول على قائمة بجميع المستخدمين | Admin |
| `GET` | `/admin/users/pending` | الحصول على المستخدمين الذين ينتظرون الموافقة | Admin |
| `POST` | `/admin/users/{id}/approve` | الموافقة على حساب مستخدم جديد | Admin |
| `PUT` | `/admin/users/{id}/status` | تفعيل أو تعطيل حساب مستخدم | Admin |
| `GET` | `/admin/orders` | الحصول على قائمة بجميع الطلبات على المنصة | Admin |
| `GET` | `/admin/products` | الحصول على قائمة بجميع المنتجات على المنصة | Admin |

## 4. نماذج البيانات (Data Transfer Objects - DTOs)

سيتم استخدام DTOs لفصل نموذج قاعدة البيانات عن نموذج الـ API، مما يوفر مرونة وأمانًا أكبر.

**مثال: `ProductDto`**
```json
{
  "id": 1,
  "name": "اسم المنتج",
  "description": "وصف المنتج",
  "price": 150.00,
  "imageUrl": "/path/to/image.jpg",
  "categoryName": "اسم الفئة",
  "brandName": "اسم العلامة التجارية",
  "vendorName": "اسم المورد"
}
```

**مثال: `RegisterDto`**
```json
{
  "accountType": "Buyer", // or "Seller"
  "fullName": "الاسم الكامل",
  "email": "user@example.com",
  "password": "كلمة المرور",
  "phoneNumber": "01234567890"
}
```

## 5. معالجة الأخطاء (Error Handling)

سيتم استخدام تنسيق موحد لرسائل الخطأ لتسهيل معالجتها في الواجهة الأمامية.

**مثال: خطأ 404 (Not Found)**
```json
{
  "statusCode": 404,
  "message": "المنتج المطلوب غير موجود",
  "timestamp": "2025-11-02T10:30:00Z"
}
```

**مثال: خطأ 400 (Bad Request - Validation Error)**
```json
{
  "statusCode": 400,
  "message": "خطأ في البيانات المدخلة",
  "errors": {
    "email": ["البريد الإلكتروني غير صحيح"],
    "password": ["كلمة المرور يجب أن تكون على الأقل 8 أحرف"]
  }
}
```

## 6. الترقيم والترتيب والتصفية (Pagination, Sorting & Filtering)

للنقاط التي ترجع قوائم (مثل `GET /products`)، سيتم استخدام Parameters في الـ Query String:

- **Pagination:** `?pageNumber=1&pageSize=10`
- **Sorting:** `?sortBy=price&sortOrder=asc`
- **Filtering:** `?categoryId=5&brandId=10`

**الاستجابة ستكون مغلفة بمعلومات الترقيم:**
```json
{
  "pageNumber": 1,
  "pageSize": 10,
  "totalPages": 5,
  "totalRecords": 50,
  "data": [
    // ... قائمة المنتجات
  ]
}
```

## 7. خاتمة

هذا التصميم يوفر بنية API قوية ومرنة لمنصة السوق البيطرية، مع التركيز على أفضل الممارسات في الأمان، الأداء، وقابلية الصيانة. سيتم توثيق جميع هذه النقاط بشكل تفصيلي باستخدام Swagger لتكون مرجعًا واضحًا لفريق التطوير.



## 8. مراجعة الشمولية وإضافة النقاط المفقودة

بعد مراجعة الـ API Design الحالي مقابل الـ 30 Use Cases، تبين أن التصميم يغطي معظم الحالات الأساسية، ولكن هناك بعض النقاط التي تحتاج إلى إضافة أو توضيح لضمان الشمولية الكاملة.

### الإضافات والتعديلات المقترحة:

#### 3.1. المصادقة (Authentication)
- **إضافة:** `POST /auth/forgot-password` لإرسال رابط إعادة تعيين كلمة المرور.
- **إضافة:** `POST /auth/reset-password` لإعادة تعيين كلمة المرور باستخدام Token.

#### 3.6. المستخدمون والملف الشخصي (Users & Profile)
- **تعديل:** يجب إضافة endpoints لإدارة عناوين الشحن بشكل كامل (تعديل وحذف).
  - `PUT /profile/addresses/{addressId}`
  - `DELETE /profile/addresses/{addressId}`

#### 3.7. لوحة تحكم المسؤول (Admin Panel)
- **إضافة:** `POST /admin/users/{id}/reject` لرفض حساب مستخدم جديد مع سبب الرفض.
- **إضافة:** `DELETE /categories/{id}` لحذف فئة (إذا لم تحتوي على منتجات).
- **إضافة:** `DELETE /brands/{id}` لحذف علامة تجارية.
- **إضافة:** `PUT /admin/products/{id}/status` لإخفاء أو إظهار منتج مخالف.

### التصميم المحدث (ملخص الإضافات):

| Method | Endpoint | Description | Authorization |
| :--- | :--- | :--- | :--- |
| `POST` | `/auth/forgot-password` | طلب إعادة تعيين كلمة المرور | Public |
| `POST` | `/auth/reset-password` | إعادة تعيين كلمة المرور | Public |
| `PUT` | `/profile/addresses/{addressId}` | تعديل عنوان شحن | Buyer |
| `DELETE` | `/profile/addresses/{addressId}` | حذف عنوان شحن | Buyer |
| `POST` | `/admin/users/{id}/reject` | رفض حساب مستخدم جديد | Admin |
| `DELETE` | `/categories/{id}` | حذف فئة | Admin |
| `DELETE` | `/brands/{id}` | حذف علامة تجارية | Admin |
| `PUT` | `/admin/products/{id}/status` | تغيير حالة منتج (مخفي/ظاهر) | Admin |

