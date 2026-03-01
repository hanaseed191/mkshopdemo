# MK Mobile Website - WordPress Implementation Guide

## 📋 ภาพรวมโครงการ

เว็บไซต์ MK Mobile เป็นเว็บไซต์สำหรับร้านจำหน่ายมือถือมือสอง ออกแบบมาเพื่อดึงดูดลูกค้าและสร้างความน่าเชื่อถือ ประกอบด้วย 4 หน้าหลัก:

1. **Home** - หน้าแรกที่แสดงภาพร้าน ผลิตภัณฑ์ และช่องทางติดต่อ
2. **About Us** - ข้อมูลเกี่ยวกับร้าน ประสบการณ์ และบริการ
3. **Location** - แสดงสาขาทั้งหมด พร้อมข้อมูลติดต่อและแผนที่
4. **Contact** - ข้อมูลติดต่อแบบละเอียด รวมถึงช่องทางต่างๆ

## 📁 ไฟล์ที่ได้รับ

```
mk-mobile/
├── mk-mobile.html    # โครงสร้าง HTML
├── style.css         # การตกแต่งทั้งหมด
├── script.js         # JavaScript สำหรับ interaction
└── README.md         # คู่มือนี้
```

## 🎨 คุณสมบัติหลัก

### ✨ การออกแบบ
- **Responsive Design** - ใช้งานได้ดีทุกอุปกรณ์
- **Modern UI** - ใช้ gradient สีสวยงาม
- **Smooth Animations** - เคลื่อนไหวลื่นไหล
- **Mobile-First** - ออกแบบสำหรับมือถือเป็นหลัก

### 🚀 ฟีเจอร์
- Navigation แบบ Sticky
- Smooth Scrolling
- Floating Action Buttons (Line & โทร)
- Image Lazy Loading
- Counter Animation สำหรับสถิติ
- Parallax Effect
- Intersection Observer Animation

### 🎯 SEO & Performance
- Semantic HTML5
- Optimized CSS
- Fast Loading
- Mobile Optimized

## 📲 วิธีนำไปใช้กับ WordPress

### วิธีที่ 1: ใช้ Custom HTML Blocks (แนะนำสำหรับผู้เริ่มต้น)

1. **ติดตั้ง Plugin:**
   - ติดตั้ง "Code Snippets" หรือ "Simple Custom CSS and JS"
   - เปิดใช้งาน

2. **เพิ่ม CSS:**
   - ไปที่ Appearance > Customize > Additional CSS
   - Copy เนื้อหาจาก `style.css` ทั้งหมดมาวาง
   - กด Publish

3. **เพิ่ม JavaScript:**
   - ใช้ Plugin "Code Snippets"
   - สร้าง Snippet ใหม่
   - Copy เนื้อหาจาก `script.js` มาวาง
   - เลือก "Run snippet everywhere"
   - Save และ Activate

4. **สร้างหน้า:**
   - สร้าง Page ใหม่
   - เลือก Template: Full Width (ไม่มี sidebar)
   - เพิ่ม Custom HTML Block
   - Copy เนื้อหาภายใน `<body>` จาก `mk-mobile.html` มาวาง
   - Publish

### วิธีที่ 2: สร้าง Custom Template

1. **เข้า Theme Editor:**
   - ไปที่ Appearance > Theme File Editor
   - สำรอง Theme ก่อนแก้ไข

2. **สร้าง Template ใหม่:**
   - สร้างไฟล์ `template-mk-mobile.php`
   - Copy โครงสร้างด้านล่าง:

```php
<?php
/*
Template Name: MK Mobile Full Page
*/
?>
<!DOCTYPE html>
<html <?php language_attributes(); ?>>
<head>
    <meta charset="<?php bloginfo('charset'); ?>">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><?php wp_title('|', true, 'right'); ?></title>
    <link rel="stylesheet" href="<?php echo get_template_directory_uri(); ?>/mk-mobile-style.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <?php wp_head(); ?>
</head>
<body <?php body_class(); ?>>
    
    <!-- วาง HTML Content ตรงนี้ -->
    
    <script src="<?php echo get_template_directory_uri(); ?>/mk-mobile-script.js"></script>
    <?php wp_footer(); ?>
</body>
</html>
```

3. **Upload ไฟล์ CSS และ JS:**
   - Upload `style.css` เป็น `mk-mobile-style.css`
   - Upload `script.js` เป็น `mk-mobile-script.js`
   - ไปที่ Theme Folder

4. **สร้างหน้าใหม่:**
   - สร้าง Page
   - เลือก Template: "MK Mobile Full Page"
   - Publish

### วิธีที่ 3: ใช้ Page Builder (Elementor/Divi)

1. **Elementor:**
   - สร้าง Page ใหม่
   - Edit with Elementor
   - เพิ่ม HTML Widget สำหรับแต่ละส่วน
   - เพิ่ม Custom CSS ใน Section Settings
   - เพิ่ม JavaScript ใน Theme Settings

2. **Divi Builder:**
   - สร้างหน้าใหม่
   - Build from Scratch
   - ใช้ Code Module
   - วาง HTML ของแต่ละส่วน
   - เพิ่ม CSS ใน Theme Options

## 🔧 การปรับแต่ง

### เปลี่ยนสี

แก้ไขใน `style.css` ที่บรรทัด 9-15:

```css
:root {
    --primary-color: #10b981;      /* สีเขียวหลัก (Emerald) */
    --secondary-color: #34d399;     /* สีเขียวสว่าง */
    --accent-color: #059669;        /* สีเขียวเข้ม */
    --text-dark: #2d3748;          /* สีตัวอักษรเข้ม */
    --text-light: #718096;         /* สีตัวอักษรอ่อน */
}
```

### เปลี่ยนรูปภาพ

ใน HTML แก้ไข `src` ของแท็ก `<img>`:

```html
<!-- เปลี่ยนจาก -->
<img src="https://via.placeholder.com/..." alt="...">

<!-- เป็น -->
<img src="<?php echo get_template_directory_uri(); ?>/images/your-image.jpg" alt="...">
```

### แก้ไขข้อความและเบอร์โทร

1. **เบอร์โทรศัพท์:** แก้ไขทุกที่ที่มี `081-234-5678`
2. **Line ID:** แก้ไข `@mkmobile`
3. **Facebook:** แก้ไข URL Messenger
4. **ที่อยู่:** แก้ไขใน Contact Section

### เพิ่ม Google Maps

แทนที่ลิงก์ Google Maps:

```html
<a href="https://maps.google.com/?q=13.7563,100.5018" target="_blank">
```

เป็น:

```html
<a href="https://www.google.com/maps/place/ที่อยู่จริงของคุณ" target="_blank">
```

หรือฝัง iframe:

```html
<iframe 
    src="https://www.google.com/maps/embed?pb=..." 
    width="100%" 
    height="400" 
    style="border:0;" 
    allowfullscreen="" 
    loading="lazy">
</iframe>
```

## 📱 ช่องทางติดต่อที่ต้องแก้ไข

จดรายการข้อมูลที่ต้องเปลี่ยนให้ครบ:

### Line Official
- [ ] ID: `@mkmobile` → `@your-line-id`
- [ ] URL: `https://line.me/ti/p/~yourid` → URL จริง

### Facebook Messenger
- [ ] URL: `https://m.me/yourpage` → URL จริง

### เบอร์โทรศัพท์
- [ ] สาขา 1: `081-234-5678`
- [ ] สาขา 2: `082-345-6789`
- [ ] ฝ่ายขาย: `081-234-5678, 081-234-5679`
- [ ] แจ้งซ่อม: `081-999-8888`
- [ ] ติดต่อทั่วไป: `081-888-7777`

### Email
- [ ] info@mkmobile.com
- [ ] repair@mkmobile.com
- [ ] feedback@mkmobile.com

### ที่อยู่สาขา
- [ ] สาขา 1: เลขที่ ถนน แขวง เขต จังหวัด รหัสไปรษณีย์
- [ ] สาขา 2: เลขที่ ถนน แขวง เขต จังหวัด รหัสไปรษณีย์

## 🎯 Checklist ก่อน Launch

### เนื้อหา
- [ ] เปลี่ยนรูปภาพทั้งหมดเป็นรูปจริง
- [ ] เช็คเบอร์โทรศัพท์ทั้งหมด
- [ ] เช็ค Line ID และ URL
- [ ] เช็ค Facebook URL
- [ ] แก้ไขที่อยู่สาขา
- [ ] ใส่ Google Maps จริง

### Technical
- [ ] ทดสอบบนมือถือหลายขนาด
- [ ] ทดสอบบนเบราว์เซอร์ต่างๆ
- [ ] เช็ค Navigation ทำงานได้
- [ ] เช็ค Floating Buttons ทำงานได้
- [ ] ทดสอบคลิกโทรออก
- [ ] ทดสอบเปิด Line และ Messenger

### SEO
- [ ] ตั้ง Title และ Meta Description
- [ ] เพิ่ม Alt Text ให้รูปภาพ
- [ ] ใส่ Schema Markup (LocalBusiness)
- [ ] Submit Sitemap

## 🐛 แก้ไขปัญหาทั่วไป

### CSS ไม่ทำงาน
1. Clear Cache ของ WordPress
2. เช็คว่าไม่มี CSS ขัดแย้งจาก Theme
3. เพิ่ม `!important` หากจำเป็น

### JavaScript ไม่ทำงาน
1. เช็ค Console ใน Browser (F12)
2. ตรวจสอบว่า jQuery ไม่ขัดแย้ง
3. ลอง Disable Plugin ทีละตัว

### Mobile ไม่ดี
1. เช็ค Viewport Meta Tag
2. ทดสอบใน Real Device
3. ใช้ Google Mobile-Friendly Test

## 🚀 เพิ่มเติม

### ติดตั้ง Analytics
เพิ่ม Google Analytics:

```html
<!-- เพิ่มก่อน </head> -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

### เพิ่ม Facebook Pixel
```html
<!-- Facebook Pixel Code -->
<script>
!function(f,b,e,v,n,t,s)
{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};
if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
n.queue=[];t=b.createElement(e);t.async=!0;
t.src=v;s=b.getElementsByTagName(e)[0];
s.parentNode.insertBefore(t,s)}(window, document,'script',
'https://connect.facebook.net/en_US/fbevents.js');
fbq('init', 'YOUR_PIXEL_ID');
fbq('track', 'PageView');
</script>
```

### Schema Markup สำหรับ SEO

เพิ่มใน `<head>`:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "MK Mobile",
  "image": "URL-รูปโลโก้",
  "telephone": "081-234-5678",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 ตลาดเซ็นทรัล",
    "addressLocality": "กรุงเทพ",
    "postalCode": "10400",
    "addressCountry": "TH"
  },
  "openingHoursSpecification": {
    "@type": "OpeningHoursSpecification",
    "dayOfWeek": [
      "Monday",
      "Tuesday",
      "Wednesday",
      "Thursday",
      "Friday",
      "Saturday",
      "Sunday"
    ],
    "opens": "10:00",
    "closes": "20:00"
  }
}
</script>
```

## 📞 ติดต่อและสนับสนุน

หากมีปัญหาหรือต้องการความช่วยเหลือเพิ่มเติม:
- ตรวจสอบ Documentation
- ดู WordPress Codex
- ถามใน WordPress Support Forum

## 📝 License

Template นี้สามารถนำไปใช้ได้เลย แก้ไขได้ตามต้องการ

---

**สร้างโดย:** Claude AI  
**วันที่:** 2024  
**Version:** 1.0
