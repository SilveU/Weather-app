# Atmosphere Weather App

A modern, high-fidelity weather dashboard built with HTML and raw CSS. 

Live Demo: [https://silveu.github.io/Weather-app/](https://silveu.github.io/Weather-app/)

## Architecture & Layout Strategy
The application is built without any external CSS frameworks, relying on a robust, native CSS architecture:
- **Global Layout (`.page`)**: A CSS Grid layout splitting the viewport into a fixed `256px` Sidebar and a fluid `1fr` Main Content area.
- **Header & Main Content**: The `.content` area is split into a fixed-height Header (for search and actions) and a `.main` container for the dashboard widgets.
- **12-Column Grid System**: The dashboard widgets inside `.main` use a 12-column CSS Grid (`repeat(12, 1fr)`). For example, the primary weather card spans 8 columns, while the radar spans 4 columns, allowing for complex, proportional layouts without hardcoded widths.
- **Assets**: 100% inline scalable SVGs mapped to CSS variables (`currentColor`) for dynamic styling.
- **Theming**: A robust CSS custom properties (`:root`) design system ready for theme switching.

## Responsive Design & Problem Solving
Making a complex CSS Grid dashboard responsive presented several challenges that were solved using a dedicated `responsive.css` file with progressive breakpoints (Tablet, Mobile, Small Mobile):

1. **The Horizontal Overflow Issue (Clipped Elements)**
   - *Problem*: On smaller screens, the page was horizontally overflowing and cutting off the right side of the widgets. This was caused by CSS Grid's default `min-width: auto` behavior, where grid items refuse to shrink smaller than their content. Specifically, the 7-day horizontal forecast flex-container was forcing its parent to stretch beyond the viewport.
   - *Solution*: Explicitly set `max-width: 100%`, `min-width: 0`, and `box-sizing: border-box` on all major layout containers. The forecast container was given `overflow: hidden` to ensure the internal horizontally-scrolling days (`overflow-x: auto`) could not push the parent container wide.

2. **The "Disappearing" Sidebar**
   - *Problem*: When transitioning to mobile, the left sidebar vanished. Attempting to move it to the bottom using `order: 2` failed because CSS Grid layout rows and `min-height: 100vh` pushed the sidebar out of the viewport entirely.
   - *Solution*: The CSS Grid on the `.page` container was disabled (`display: block`) on mobile. The `.sidebar` was then converted into a professional **Sticky Bottom Navigation Bar** using `position: fixed; bottom: 0; width: 100%;`, with `padding-bottom` applied to the page to prevent content from being hidden behind the nav.

## Roadmap (To-Do)
The UI layout is complete and fully responsive, but the app needs logic and dynamic data:
- [x] **Mobile Responsiveness**: Custom media queries, bottom navigation, and horizontal scroll constraints.
- [ ] **API Integration**: Connect to a live weather provider (e.g., OpenWeatherMap) to fetch real-time data.
- [ ] **Search Logic**: Implement the location search functionality.
- [ ] **Interactive Radar**: Replace the radar placeholder with a working Map API (e.g., Leaflet.js).
- [ ] **State Management**: JavaScript to handle dynamic DOM updates, day switching, and active states.

---

# تطبيق طقس Atmosphere 🌤️

مشروع تطبيق طقس خفيف وسريع، مبني من الصفر بـ HTML و CSS بس، من غير ما أستخدم أي مكتبات جاهزة (زي Bootstrap أو غيره). الفكرة كلها إني أعمل ديزاين رايق ونظيف، وأركز على تفاصيل الـ UI/UX.

رابط الموقع لايف: [https://silveu.github.io/Weather-app/](https://silveu.github.io/Weather-app/)

## إزاي بنيت الديزاين ده؟ (Architecture)
حبيت أتحدى نفسي وأعمل الهيكلة كلها بـ Native CSS:
- **نظام الـ Grid**: الصفحة كلها متقسمة بـ `CSS Grid`. القائمة الجانبية (Sidebar) واخدة مساحة ثابتة `256px`، وباقي الشاشة للمحتوى الأساسي.
- **التقسيمة الداخلية (12 عمود)**: جوه الـ `.main`، استخدمت شبكة من 12 عمود (`repeat(12, 1fr)`). ده خلاني أقدر أوزع الكروت براحتي؛ كارت الطقس الأساسي واخد 8 أعمدة، والرادار واخد 4. نظام مرن جداً ومريح في التوزيع.
- **أيقونات الـ SVG**: مفيش صور خارجية، كل الأيقونات `Inline SVG` ومربوطة بمتغيرات الألوان (`currentColor`) عشان تتلون أوتوماتيك مع الـ Theme.
- **ألوان جاهزة (Theming)**: مجهز كل الألوان في `:root` كمتغيرات، وده بيسهل جداً لو حبيت أضيف Dark/Light Mode بعدين.

## مشاكل قابلتني في الـ Responsive وإزاي حليتها 🛠️
تحويل داشبورد مليانة كروت لـ Mobile View مكنش سهل، دي أبرز المشاكل اللي حليتها في ملف `responsive.css`:

1. **مشكلة السكرول الأفقي المزعج (Horizontal Overflow)**
   - *إيه اللي حصل؟* الشاشة على الموبايل كانت بتعمل سكرول بالعرض، وفيه عناصر كانت مقطوعة من اليمين. السبب كان كارت الـ (7 أيام)؛ لأن العناصر جواه كانت بترفض تصغر عن حجمها بسبب خاصية `min-width: auto` الافتراضية في الـ Grid، فكانت بتزق الصفحة وتطلعها برا الشاشة.
   - *الحل:* فرضت `max-width: 100%` و `min-width: 0` على كل الحاويات الأساسية. والأهم إني ضفت `overflow: hidden` لكارت الـ (7 أيام) عشان أعمل سكرول داخلي للأيام (`overflow-x: auto`) من غير ما الكارت نفسه يزق بقية الديزاين.

2. **اختفاء القائمة الجانبية (The Missing Sidebar)**
   - *إيه اللي حصل؟* لما صغرت الشاشة، حاولت أنزل الـ Sidebar تحت باستخدام `order: 2` في الـ Grid، بس اختفت تماماً تحت الشاشة بسبب إعدادات الـ `min-height: 100vh` للموقع.
   - *الحل:* لغيت الـ Grid خالص في وضع الموبايل (`display: block`)، وحولت الـ Sidebar لـ **Bottom Navigation Bar** (شريط تنقل سفلي زي أبلكيشنز الموبايل) بيثبت تحت بـ `position: fixed; bottom: 0;`، وضفت مساحة فاضية آخر الصفحة عشان المحتوى ميتغطاش.

## الخطوات الجاية (الـ Roadmap) 🚀
الديزاين والتجاوب (UI/UX) خلصوا 100%، الباقي شوية برمجة وربط بيانات:
- [x] **تجاوب الموبايل**: ظبطت الـ Media Queries وشريط التنقل السفلي.
- [ ] **ربط API الطقس**: هربط الموقع بـ OpenWeatherMap عشان يعرض داتا حقيقية.
- [ ] **تفعيل البحث**: أبرمج شريط البحث عشان يجيب طقس أي مدينة.
- [ ] **الرادار الحقيقي**: أبدل صندوق الرادار الحالي بخريطة حقيقية تفاعلية بـ Leaflet.js.
- [ ] **إدارة الحالة (State Management)**: شوية JavaScript عشان أغير الأيام والبيانات ديناميكياً.
