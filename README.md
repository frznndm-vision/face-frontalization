# face-frontalization
# پروژه: مقایسه مدل‌های Face Frontalization / Face Frontalization-Related Tasks

## مقدمه
در این پروژه، چندین مدل Open-Source را برای تسک frontalization (یا Face Reenactment / Animation) اجرا کرده‌ایم و خروجی‌های آن‌ها را از نظر کیفیت، سرعت اجرای مدل، نیاز به منابع و سایر معیارها با هم مقایسه کرده‌ایم.

## مدل‌های بررسی‌شده
1. **FacePoke** – ابزار تعامل مستقیم با تصویر برای جابه‌جایی سر مبتنی بر LivePortrait (Hugging Face Space) :contentReference[oaicite:6]{index=6}  
2. **LivePortrait** – مدل انیمیشن پرتره کارآمد با قابلیت‌های Stitching و Retarget Control :contentReference[oaicite:7]{index=7}  
3. **AniPortrait** – انیمیشن پرتره مبتنی بر صدا با امکان face reenactment :contentReference[oaicite:8]{index=8}  
4. **FSRT** – فریم‌ورک CVPR 2024 برای face reenactment با در نظر گرفتن HEAD-POSE، EMOTIONS و APPEARANCE :contentReference[oaicite:9]{index=9}  
5. **scaleway/frontalization** – پیاده‌سازی GAN برای frontalization با DALI برای پردازش سریع داده‌ها :contentReference[oaicite:10]{index=10}  
6. **FFWM** – مدل warp مبتنی بر جریان برای frontalization با نظارت نوری متفاوت (ECCV 2020) :contentReference[oaicite:11]{index=11}

## معیارهای مقایسه
| مدل | سرعت اجرا (FPS) | کیفیت خروجی | پیچیدگی نصب | استفاده از GPU/Resource | نکات خاص |
|------|------------------|--------------|--------------|--------------------------|------------|
| FacePoke | – | تعاملی، LiveDemo | Docker / محلی | نیاز GPU | مناسب تعامل |
| LivePortrait | – | طبیعی | نیاز به Conda/FFmpeg | متوسط | پشتیبانی از حیوانات |
| AniPortrait | – | صوت به تصویر | CLI + Gradio | وزن‌های pretrained | پشتیبانی از audio-driven |
| FSRT | – | رونویسی دقیق حرکت | PyTorch + face-alignment | بالا | motion relative/absolute |
| scaleway | – | frontalization GAN | PyTorch + DALI | متوسط | توضیحات کامل داده‌ها |
| FFWM | – | warp-based | PyTorch 1.5 + setup.sh | متوسط | توجه به نورپردازی inconsistent |

**نکته:** مقادیر دقیق (FPS، امتیاز کیفیت، یا metrics عددی) باید پس از اجرای مدل‌ها وارد شود.

## نتایج
در این بخش تصاویر خروجی، جدول امتیازها، نظرات یا... قرار می‌گیرد (مثلاً FID, SSIM, سرعت اجرا).

## نتیجه‌گیری
مثلاً:
- مدل‌های صوتی مانند AniPortrait برای جلوه‌های سینماتیک مناسب هستند.
- FSRT دقت بالایی در انتقال حالت دارد.
- مدل‌های GAN مانند scaleway و FFWM در frontalization عملکرد خوبی ارائه داده‌اند.

## نحوه اجرا
برای هر مدل، مراحل نصب و اجرا رو لیست کنید:
- Clone repo
- نصب وابستگی‌ها
- نحوه اجرا (CLI یا اسکریپت)
- توجه به GPU یا فایل‌های pretrained

## منابع و استناد
در آخر:

