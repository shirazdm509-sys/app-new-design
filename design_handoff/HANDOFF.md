# Handoff: نرم افزار آیت الله دستغیب — UI Design

## Overview
این پکیج شامل طراحی کامل رابط کاربری نرم‌افزار **آیت الله دستغیب** است. اپلیکیشن یک کتابخانه دیجیتال اسلامی است که شامل کتاب‌ها، سخنرانی‌ها، صوت، ویدیو، پرسش و پاسخ و پخش زنده می‌شود.

## About the Design Files
فایل‌های این پکیج **نمونه‌های طراحی در HTML** هستند — پروتوتایپ‌های high-fidelity که ظاهر و رفتار مورد نظر را نشان می‌دهند. وظیفه شما این است که این طراحی‌ها را در محیط کدبیس واقعی (React Native / Flutter / Android Native) با استفاده از پترن‌ها و کتابخانه‌های موجود بازسازی کنید.

## Fidelity
**High-Fidelity** — رنگ‌ها، تایپوگرافی، فاصله‌ها و تعاملات دقیق هستند. UI باید pixel-perfect بازسازی شود.

---

## Design System

### رنگ‌ها (CSS Variables → کد واقعی)

```
Background:
  --bg:          #f8f5f0   (پس‌زمینه اصلی — کرم گرم)
  --bg-soft:     #f5f1eb
  --bg-deep:     #ede8e0
  --card:        #fefcf9   (کارت‌ها)
  --border-soft: #e0d8cc
  --border:      #cfc5b5

Text:
  --ink:         #2a2018   (متن اصلی)
  --ink-2:       #5a4e3e   (متن ثانوی)
  --ink-3:       #8a7a6a   (متن ضعیف)
  --ink-4:       #a89888   (placeholder)

Green (accent اصلی):
  --green:       #4a7c65
  --green-deep:  #2e5241
  --green-soft:  #8cb8a0
  --green-wash:  #eef6f1

Gold (تزیینی):
  --gold:        #b89a5a
  --gold-deep:   #8a6e32
  --gold-wash:   #faf4e8

Category Colors:
  --cat-1:       #c47a54   (ترکوتا — سخنرانی‌ها)
  --cat-2:       #5a7ea0   (آبی خاکی — تفسیر)
  --cat-3:       #7a68a0   (بنفش ملایم — محرم)
  --cat-4:       #5a8870   (سبز خاکی — مناسبت‌ها)
```

### فونت‌ها
```
فارسی/عربی UI:    Vazirmatn (وزیرمتن) — وزن‌های 400، 500، 600، 700
متن عربی (آیات):  Amiri — وزن‌های 400، 700
CDN: https://cdn.jsdelivr.net/gh/rastikerdar/vazirmatn@v33.003/Vazirmatn-font-face.css
     https://fonts.googleapis.com/css2?family=Amiri:wght@400;700
```

### Border Radius
```
xs: 6px
sm: 10px
md: 14px
lg: 20px
xl: 28px
```

### سایه‌ها
```
sh-1: 0 1px 2px rgba(40,32,24,0.04), 0 2px 6px rgba(40,32,24,0.04)
sh-2: 0 2px 4px rgba(40,32,24,0.05), 0 8px 24px rgba(40,32,24,0.06)
sh-3: 0 4px 8px rgba(40,32,24,0.06), 0 16px 40px rgba(40,32,24,0.08)
```

---

## Screens / Views

### ۱. خانه (Home)

**Layout (موبایل):**
- Header: Logo + نام + آیکون‌های جستجو و اعلان (ارتفاع ۶۰px)
- Hero Carousel: کارت gradient سبز تیره (ارتفاع ۱۸۰px، radius 20px)، الگوی هندسی اسلامی با opacity 0.08
- Quick Grid: 4×2 آیکون (gap 8px)، هر آیکون ۴۲×۴۲px، radius 12px
- Sections: عنوان (خط سبز ۳px + متن ۱۵px bold) + CTA
- Books: اسکرول افقی، کارت‌های ۱۰۸×۱۴۸px
- Images Grid: gridTemplateColumns: 2fr 1fr 1fr × 2ردیف
- Video Rows: thumbnail 112×72px + عنوان + بازدید
- Audio Rows: دایره ۴۰px پخش + عنوان + مدت
- Post Rows: آیکون ۴۸×۴۸px + chip دسته‌بندی + عنوان
- Bottom Nav: ۵ آیتم، نشانگر سبز ۳×۲۸px بالای آیکون فعال

**مهم:** direction: rtl روی همه المان‌ها

---

### ۲. کتابخانه (Library)

**Layout (موبایل):**
- Header: عنوان «کتابخانه» + آیکون‌های جستجو و گرید
- Filter Chips: اسکرول افقی، pill shape (radius 100px)
  - فعال: background: --green-deep, color: white
  - غیرفعال: border: 1px solid --border, background: --card
- Grid: 3 ستونه، aspectRatio: 3/4 برای جلد کتاب
- جلد کتاب:
  - gradient رنگی خاکی
  - فریم داخلی: inset 5px، border طلایی با opacity 0.4
  - نوار کناری راست ۳px تیره‌تر (شبیه ستون کتاب)
  - نشان دانلود شده: دایره ۲۲px سبز + تیک
- Bottom Nav: همان الگو

---

### ۳. فهرست کتاب (Book Index)

**Layout (موبایل):**
- Header: دکمه برگشت + عنوان کتاب + آیکون نشانک و منو
- Progress Card:
  - gradient سبز ملایم، border سبز نرم
  - thumbnail جلد ۷۲×۹۶px + پیشرفت‌بار
  - دکمه «ادامه مطالعه»: سبز تیره، radius 14px
- Tabs: ۳ تب (فهرست/نشان‌ها/یادداشت‌ها)
  - فعال: border-bottom ۲px سبز، رنگ سبز تیره، bold
- Chapter List:
  - دایره شماره ۳۲px (سبز اگر خوانده، سبز پر اگر فعال)
  - divider خط ۱px بین آیتم‌ها

---

### ۴. خواندن کتاب (Reading)

**Layout (موبایل):**
- Header: برگشت + عنوان وسط + آیکون‌های قلم/نشانک
- تزیین: SVG خطوط طلایی و لوزی وسط صفحه
- کارت آیه عربی:
  - background: --card، border نرم
  - font-family: Amiri, fontSize: 21px, lineHeight: 2.1
  - عنوان آیه: سبز کم‌رنگ یا طلایی، fontSize: 10px
- متن ترجمه: fontSize 14.5px, lineHeight: 2, textAlign: justify
- کلمات کلیدی: رنگ --gold-deep، fontWeight: 700
- Slider کنترل صفحه: در پایین، با thumb دایره ۱۴px

---

### ۵. رسانه (Media)

**Layout (موبایل):**
- Tab Switcher سه‌تایی: فیلم/صوت/عکس
  - فعال: background card، border سبز، رنگ سبز
- Category Grid: 2 ستونه، هر کارت minHeight 140px
  - آیکون پوشه‌مانند SVG با gradient رنگی
  - عنوان category + تعداد مورد

---

### ۶. سخنرانی‌ها (Lectures)

**Layout (موبایل):**
- Grid 2×2 کارت‌های مربعی (aspectRatio: 1/1.1)
  - هر کارت: gradient تیره + الگوی هندسی SVG opacity 0.08 + نماد فارسی
  - عنوان + تعداد جلسه در پایین کارت
- لیست «آخرین سخنرانی‌ها» زیر grid

---

### ۷. ورود / ثبت‌نام (Auth)

**Layout (موبایل):**
- BrandMark دایره ۷۲px وسط
- Tab Switcher ورود/ثبت‌نام: pill inside pill
- فیلدها: label + input (border 1px، radius 14px، padding 12px)
- دکمه اصلی: --green-deep، text سفید، radius 14px
- Divider: خط + «یا»
- دکمه ثانوی: border 1px، background: --card

---

### ۸. پخش‌کننده صوت (Player)

**Layout (موبایل — full screen):**
- background: gradient سبز تیره (0.32→0.22 oklch)
- Header: down arrow + نام playlist + dots menu
- Artwork: مربع با radius 28px، gradient، الگوی هندسی اسلامی SVG
- Track info: عنوان ۱۷px bold + هنرمند ۱۲px مات
- Progress bar: height 3px، thumb دایره ۱۲px طلایی
- Transport: share | skip-forward | pause(62px دایره طلایی) | skip-back | download

---

## ساختار Layout تبلت و دسکتاپ

### تبلت (1024×768 landscape)
- Sidebar ثابت ۲۲۰px سمت راست با nav items + live card
- Content area سیال در سمت چپ
- Reading: ۲ ستون (عربی | ترجمه فارسی) در پنل مرکزی
- Library: ۵ ستون grid

### دسکتاپ (1280×800)
- Top navbar: logo + nav items + search bar + bell + user
- Content: maxWidth 1200px، margin auto، padding 40px
- Home hero: 2fr+1fr grid (hero card + reading progress card)
- Reading: ۳ پنل (فهرست فصول | متن اصلی | یادداشت‌ها)
- Footer ساده با حقوق + لینک‌ها

---

## Interactions & Behavior

### ناوبری
- موبایل: Bottom Tab Bar با ۵ آیتم
- تبلت: Side Rail ثابت
- دسکتاپ: Top Nav Bar

### انیمیشن‌ها
- transition همه hover states: 0.15s ease
- کارت‌ها: hover → box-shadow عمیق‌تر + translateY(-2px)
- Bottom nav active: نشانگر سبز با transition عرض
- Chip filter: transition background + color

### حالت‌های خاص
- کتاب دانلود شده: badge سبز تیک دار روی جلد
- در حال دانلود: badge سفید با آیکون دانلود
- پیشرفت مطالعه: progress bar سبز
- آیتم فعال navbar: رنگ سبز تیره + وزن ۶۰۰+

---

## Assets / Icons

آیکون‌ها همه **stroke-based SVG** هستند (viewBox 0 0 24 24)، رنگ از `currentColor`:
- Home، Book، Media، Mic، Question، Search، Bell، Bookmark، Note، List، Grid
- Play، Pause، SkipForward، SkipBack، Volume، Share، Download
- User، Login، Settings، Menu، Dots، Close، Plus، Check
- ChevronLeft/Right/Down، ArrowLeft/Right
- News، Broadcast، Pay، Mosque، Contact، Bio، Social
- Image، Headphones، Calendar، Folder
- Ornament (ستاره تزیینی)، DecoDivider (خط تزیینی با لوزی طلایی)

**BrandMark:** دایره ۳۶px، gradient سبز، حرف «د» سفید/کرم — قابل جایگزینی با لوگوی رسمی

---

## الگوهای تزیینی اسلامی

در hero card ها و artwork پخش‌کننده از SVG pattern استفاده شده:
```html
<!-- الگوی لوزی -->
<pattern id="geo" x="0" y="0" width="40" height="40" patternUnits="userSpaceOnUse">
  <path d="M20 0 L40 20 L20 40 L0 20 Z" fill="none" stroke="#fff" strokeWidth="1"/>
  <circle cx="20" cy="20" r="3" fill="#fff"/>
</pattern>
```
opacity روی پترن: 0.08 تا 0.12

---

## Files در این پکیج

| فایل | محتوا |
|------|-------|
| `tokens.css` | CSS variables، فونت، scrollbar، utility classes |
| `icons.jsx` | همه آیکون‌های SVG به صورت React component |
| `screens/mobile.jsx` | Home، SectionHeader، BookCard، VideoRow، AudioRow، PostRow، BrandMark، MobileBottomNav، MobileHeader |
| `screens/mobile2.jsx` | Library، BookIndex، Reading، Media، Lectures، Login، Player |
| `screens/tablet.jsx` | TabletHome، TabletLibrary، TabletReading |
| `screens/desktop.jsx` | DesktopHome، DesktopReading |
| `index.html` | Canvas اصلی — همه صفحات کنار هم |

---

## دستورالعمل پیاده‌سازی

1. **شروع از موبایل:** صفحه خانه را اول پیاده کنید
2. **direction: rtl** را روی root تنظیم کنید
3. فونت **Vazirmatn** را نصب و برای همه متون فارسی استفاده کنید
4. **رنگ‌های CSS variable** را در theme/tokens پروژه ثبت کنید
5. کامپوننت‌های مشترک را ابتدا بسازید: `BottomNav`، `Header`، `SectionHeader`، `BookCard`، `VideoRow`، `AudioRow`
6. صفحه به صفحه پیش بروید، نه همه یکجا
7. داده‌های mock را hardcode کنید — بعداً به API وصل کنید
8. آیکون‌های SVG در `icons.jsx` را می‌توانید مستقیم کپی کنید

---

*طراحی شده در آوریل ۱۴۰۵ — آماده برای پیاده‌سازی*
