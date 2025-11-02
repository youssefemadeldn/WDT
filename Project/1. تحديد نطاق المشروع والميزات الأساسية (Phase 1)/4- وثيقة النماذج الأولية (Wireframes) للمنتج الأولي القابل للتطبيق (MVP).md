_No response_TEXT = """
# وثيقة النماذج الأولية (Wireframes) للمنتج الأولي القابل للتطبيق (MVP)

## 1. مقدمة

هذه الوثيقة تحتوي على وصف نصي للنماذج الأولية (Wireframes) لجميع شاشات المنتج الأولي القابل للتطبيق (MVP). كل Wireframe يمثل الهيكل الأساسي لصفحة أو واجهة معينة في النظام، مع التركيز على ترتيب العناصر والوظائف بدلاً من التصميم الجمالي.

---

## 2. Wireframes للمستخدم العام (Public User)

### 2.1. الصفحة الرئيسية (Homepage)

```
+----------------------------------------------------+
| [Logo] [Home] [Products] [About Us] [Login] [Register] |
+----------------------------------------------------+
|                                                    |
|                  [Hero Image/Banner]                 |
|                                                    |
+----------------------------------------------------+
|                                                    |
|                 Featured Categories                  |
| [Category 1] [Category 2] [Category 3] [Category 4]  |
|                                                    |
+----------------------------------------------------+
|                                                    |
|                  Featured Products                   |
| [Product 1] [Product 2] [Product 3] [Product 4]    |
|                                                    |
+----------------------------------------------------+
| [Footer: About, Contact, Terms]                    |
+----------------------------------------------------+
```

### 2.2. صفحة التسجيل (Registration Page)

```
+----------------------------------------------------+
| [Logo]                                             |
+----------------------------------------------------+
|                                                    |
|                   Create an Account                  |
|                                                    |
|  Account Type: [ ( ) Buyer ] [ ( ) Seller ]        |
|                                                    |
|  [Full Name/Company Name]                          |
|  [Email Address]                                   |
|  [Password]                                        |
|  [Confirm Password]                                |
|  [Phone Number]                                    |
|  [Address/Company Address]                         |
|  (Seller Only) [Commercial Registration No.]       |
|                                                    |
|  [ ] I agree to the Terms and Conditions           |
|                                                    |
|  [Create Account Button]                           |
|                                                    |
|  Already have an account? [Login]                  |
|                                                    |
+----------------------------------------------------+
```

### 2.3. صفحة تسجيل الدخول (Login Page)

```
+----------------------------------------------------+
| [Logo]                                             |
+----------------------------------------------------+
|                                                    |
|                       Login                        |
|                                                    |
|  [Email Address]                                   |
|  [Password]                                        |
|                                                    |
|  [ ] Remember Me      [Forgot Password?]           |
|                                                    |
|  [Login Button]                                    |
|                                                    |
|  Don't have an account? [Register]                 |
|                                                    |
+----------------------------------------------------+
```

### 2.4. صفحة استعادة كلمة المرور (Forgot Password Page)

```
+----------------------------------------------------+
| [Logo]                                             |
+----------------------------------------------------+
|                                                    |
|                  Reset Password                    |
|                                                    |
|  [Email Address]                                   |
|                                                    |
|  [Send Reset Link Button]                          |
|                                                    |
+----------------------------------------------------+
```

---

## 3. Wireframes للمشتري (Buyer)

### 3.1. صفحة قائمة المنتجات (Product Listing Page)

```
+----------------------------------------------------+
| [Logo] [Search Bar] [My Account] [Cart (3)] [Logout] |
+----------------------------------------------------+
| [Home] > [Category Name]                           |
+----------------------------------------------------+
| Filters:                                           |
| - Category: [Dropdown]                             |
| - Sort by: [Price, Name]                           |
+----------------------------------------------------+
| [Product Image]      [Product Image]      [Product Image] |
| [Product Name]       [Product Name]       [Product Name]  |
| [Price]              [Price]              [Price]         |
| [Seller Name]        [Seller Name]        [Seller Name]   |
| [Add to Cart]        [Add to Cart]        [Add to Cart]   |
+----------------------------------------------------+
| [Pagination: 1, 2, 3, ...]                         |
+----------------------------------------------------+
```

### 3.2. صفحة تفاصيل المنتج (Product Details Page)

```
+----------------------------------------------------+
| [Logo] [Search Bar] [My Account] [Cart (3)] [Logout] |
+----------------------------------------------------+
| [Home] > [Category] > [Product Name]               |
+----------------------------------------------------+
| [Product Image]      |  Product Name                |
|                      |  Seller: [Seller Name]       |
|                      |  Price: [Price]              |
|                      |  Availability: [In Stock]    |
|                      |  Quantity: [ 1 ] [+][-]      |
|                      |  [Add to Cart Button]        |
+----------------------|------------------------------+
| Description:                                       |
| [Long product description text...]                 |
+----------------------------------------------------+
| Specifications:                                    |
| [Product specifications details...]                |
+----------------------------------------------------+
```

### 3.3. صفحة عربة التسوق (Shopping Cart Page)

```
+----------------------------------------------------+
| [Logo] [Search Bar] [My Account] [Cart (3)] [Logout] |
+----------------------------------------------------+
|                     Shopping Cart                    |
+----------------------------------------------------+
| Product         | Price   | Quantity | Total      |
|-----------------|---------|----------|------------|
| [Image] P. Name | [Price] | [ 2 ]    | [Total]    | [Remove] |
| [Image] P. Name | [Price] | [ 1 ]    | [Total]    | [Remove] |
+----------------------------------------------------+
|                                 Subtotal: [Amount] |
|                                                    |
| [Continue Shopping]     [Proceed to Checkout]      |
+----------------------------------------------------+
```

### 3.4. صفحة إتمام الطلب (Checkout Page)

```
+----------------------------------------------------+
| [Logo]                                             |
+----------------------------------------------------+
|                       Checkout                       |
+----------------------------------------------------+
| Shipping Address:                                  |
| [List of saved addresses] or [Add New Address]     |
|----------------------------------------------------|
| Payment Method:                                    |
| [ ( ) Cash on Delivery ]                           |
| [ ( ) Bank Transfer ]                              |
| [ ( ) Online Payment (Paymob) ]                    |
|----------------------------------------------------|
| Order Summary:                                     |
| [Product 1] x2 ....................... [Price]    |
| [Product 2] x1 ....................... [Price]    |
| Subtotal: ............................ [Amount]   |
| Shipping: ............................ [Amount]   |
| Total: ............................... [Amount]   |
|----------------------------------------------------|
|                      [Confirm Order Button]          |
+----------------------------------------------------+
```

### 3.5. لوحة تحكم المشتري (Buyer Dashboard)

```
+----------------------------------------------------+
| [Logo] [Search Bar] [My Account] [Cart (3)] [Logout] |
+----------------------------------------------------+
| My Account                                         |
+----------------------------------------------------+
| [Profile]                                          |
| [My Orders]                                        |
| [Shipping Addresses]                               |
| [Logout]                                           |
+----------------------------------------------------+
|                      Recent Orders                   |
| Order # | Date       | Status      | Total        |
|---------|------------|-------------|--------------|
| 12345   | 2025-11-01 | Shipped     | [Amount]     |
| 12344   | 2025-10-28 | Delivered   | [Amount]     |
+----------------------------------------------------+
```

---

## 4. Wireframes للبائع (Seller)

### 4.1. لوحة تحكم البائع (Seller Dashboard)

```
+----------------------------------------------------+
| [Logo] [My Account] [Logout]                       |
+----------------------------------------------------+
| Seller Dashboard                                   |
+----------------------------------------------------+
| [Dashboard]                                        |
| [My Products]                                      |
| [My Orders]                                        |
| [Profile]                                          |
+----------------------------------------------------+
|                      Quick Stats                     |
| Total Sales | Orders Today | Products | Pending Orders |
|-------------|--------------|----------|----------------|
| [Amount]    | [Number]     | [Number] | [Number]       |
+----------------------------------------------------+
|                      Recent Orders                   |
| Order # | Date       | Status      | Total        |
|---------|------------|-------------|--------------|
| 12345   | 2025-11-01 | New         | [Amount]     |
+----------------------------------------------------+
```

### 4.2. صفحة إدارة المنتجات (Seller - Product Management)

```
+----------------------------------------------------+
| [Logo] [My Account] [Logout]                       |
+----------------------------------------------------+
| My Products               [Add New Product Button] |
+----------------------------------------------------+
| Product         | Price   | Stock | Status     | Actions |
|-----------------|---------|-------|------------|---------|
| [Image] P. Name | [Price] | [Qty] | [Active]   | [Edit] [Delete] |
| [Image] P. Name | [Price] | [Qty] | [Inactive] | [Edit] [Delete] |
+----------------------------------------------------+
```

### 4.3. صفحة إضافة/تعديل منتج (Seller - Add/Edit Product)

```
+----------------------------------------------------+
| [Logo] [My Account] [Logout]                       |
+----------------------------------------------------+
|                  Add/Edit Product                    |
+----------------------------------------------------+
|  [Product Name]                                    |
|  [Product Description (Text Area)]                 |
|  [Price]                                           |
|  [Stock Quantity]                                  |
|  Category: [Dropdown]                              |
|  Upload Images: [Choose Files Button]              |
|                                                    |
|  [Save Product Button]                             |
+----------------------------------------------------+
```

### 4.4. صفحة إدارة الطلبات (Seller - Order Management)

```
+----------------------------------------------------+
| [Logo] [My Account] [Logout]                       |
+----------------------------------------------------+
| My Orders                                          |
+----------------------------------------------------+
| Order # | Date       | Buyer Name | Status      | Total  |
|---------|------------|------------|-------------|--------|
| 12345   | 2025-11-01 | [Name]     | [New]       | [Amount] |
| 12343   | 2025-10-30 | [Name]     | [Shipped]   | [Amount] |
+----------------------------------------------------+
```

### 4.5. صفحة تفاصيل الطلب (Seller - Order Details)

```
+----------------------------------------------------+
| [Logo] [My Account] [Logout]                       |
+----------------------------------------------------+
| Order Details #12345                               |
+----------------------------------------------------+
| Buyer: [Name] | Date: [Date] | Total: [Amount]    |
|----------------------------------------------------|
| Shipping Address:                                  |
| [Full Address]                                     |
|----------------------------------------------------|
| Products:                                          |
| [Product 1] x2                                     |
| [Product 2] x1                                     |
|----------------------------------------------------|
| Current Status: [New]                              |
| Update Status: [Dropdown: Confirmed, Shipped, Completed] [Update] |
+----------------------------------------------------+
```

---

## 5. Wireframes للمسؤول (Admin Panel)

### 5.1. لوحة تحكم المسؤول (Admin Dashboard)

```
+----------------------------------------------------+
| [Logo] [Admin Name] [Logout]                       |
+----------------------------------------------------+
| Admin Dashboard                                    |
+----------------------------------------------------+
| [Dashboard]                                        |
| [User Management]                                  |
| [Product Management]                               |
| [Order Management]                                 |
| [Categories]                                       |
+----------------------------------------------------+
|                      Platform Stats                  |
| Total Users | Total Products | Total Orders | Total Sales |
|-------------|----------------|--------------|-------------|
| [Number]    | [Number]       | [Number]     | [Amount]    |
+----------------------------------------------------+
|                 Pending User Approvals               |
| User Name | Type   | Date       | Actions          |
|-----------|--------|------------|------------------|
| [Name]    | Seller | [Date]     | [Approve] [Reject] |
+----------------------------------------------------+
```

### 5.2. صفحة إدارة المستخدمين (Admin - User Management)

```
+----------------------------------------------------+
| [Logo] [Admin Name] [Logout]                       |
+----------------------------------------------------+
| User Management                                    |
+----------------------------------------------------+
| Filter by: [Type, Status] [Search by Email]        |
+----------------------------------------------------+
| User Name | Email         | Type   | Status     | Actions |
|-----------|---------------|--------|------------|---------|
| [Name]    | [Email]       | Buyer  | [Active]   | [View] [Disable] |
| [Name]    | [Email]       | Seller | [Pending]  | [View] [Approve] |
+----------------------------------------------------+
```

### 5.3. صفحة إدارة الفئات (Admin - Category Management)

```
+----------------------------------------------------+
| [Logo] [Admin Name] [Logout]                       |
+----------------------------------------------------+
| Category Management       [Add New Category Button] |
+----------------------------------------------------+
| Category Name | Product Count | Actions            |
|---------------|---------------|--------------------|
| [Name]        | [Number]      | [Edit] [Delete]    |
| [Name]        | [Number]      | [Edit] [Delete]    |
+----------------------------------------------------+
```

"""
