# face-frontalization
# پروژه: مقایسه مدل‌های Face Frontalization / Face Frontalization-Related Tasks

## مقدمه
در این پروژه، چندین مدل Open-Source را برای تسک **Frontalization** (یا Face Reenactment / Animation) اجرا کرده‌ایم و خروجی‌های آن‌ها را از نظر کیفیت، سرعت اجرای مدل، نیاز به منابع و سایر معیارها با هم مقایسه کرده‌ایم.

---

## مدل‌های بررسی‌شده
1. [**FacePoke**](https://github.com/jbilcke-hf/FacePoke) – ابزار تعامل مستقیم با تصویر برای جابه‌جایی سر مبتنی بر LivePortrait (Hugging Face Space).  
2. [**LivePortrait**](https://github.com/KwaiVGI/LivePortrait) – مدل انیمیشن پرتره کارآمد با قابلیت‌های Stitching و Retarget Control.  
3. [**AniPortrait**](https://github.com/Zejun-Yang/AniPortrait/tree/main) – انیمیشن پرتره مبتنی بر صدا با امکان Face Reenactment.  
4. [**FSRT**](https://github.com/andrerochow/fsrt) – فریم‌ورک CVPR 2024 برای Face Reenactment با در نظر گرفتن HEAD-POSE، EMOTIONS و APPEARANCE.  
5. [**scaleway/frontalization**](https://github.com/scaleway/frontalization) – پیاده‌سازی GAN برای Frontalization با DALI برای پردازش سریع داده‌ها.  
6. [**FFWM**](https://github.com/csyxwei/FFWM) – مدل warp مبتنی بر جریان برای Frontalization با نظارت نوری متفاوت (ECCV 2020).  

---

## معیارهای مقایسه
| مدل              | سرعت اجرا (FPS) | کیفیت خروجی | پیچیدگی نصب          | استفاده از GPU/Resource | نکات خاص |
|------------------|------------------|--------------|----------------------|--------------------------|-----------|
| FacePoke         | –                | تعاملی، LiveDemo | Docker / محلی       | نیاز GPU                 | مناسب تعامل زنده |
| LivePortrait     | –                | طبیعی       | Conda + FFmpeg       | متوسط                    | پشتیبانی از حیوانات |
| AniPortrait      | –                | صوت به تصویر | CLI + Gradio         | وزن‌های pretrained       | Audio-Driven |
| FSRT             | –                | دقیق         | PyTorch + face-alignment | بالا                 | Motion relative/absolute |
| scaleway         | –                | GAN          | PyTorch + DALI       | متوسط                    | پیاده‌سازی GAN کلاسیک |
| FFWM             | –                | warp-based   | PyTorch 1.5 + setup.sh | متوسط                  | مناسب نورپردازی نامتوازن |

**نکته:** مقادیر دقیق (FPS، امتیاز کیفیت، یا metrics عددی) باید پس از اجرای عملی وارد شود.

---

## نحوه اجرا

### FacePoke
ابزار real-time برای تغییر حالت سر و صورت روی پرتره‌ها (مبتنی بر LivePortrait).  

#### پیش‌نیاز
- Linux + Python 3.10 + CUDA 12.4 (NVIDIA GPU)  
- Git LFS:
نصب محلیgit clone https://github.com/jbilcke-hf/FacePoke.git
cd FacePoke
pip3 install --upgrade -r requirements.txt

cd client
bun install
bun build ./src/index.tsx --outdir ../public/
cd ..

python app.py
# سپس مرورگر: http://localhost:8080


اجرای Dockerdocker build -t facepoke .
docker run -p 8080:8080 facepoke

نکات

توسعه‌دهنده فقط روی Linux (Python 3.10 + CUDA 12.4) تست کرده است.

روی Apple Silicon برخی کاربران خطای «Failed to initialize face detection» گزارش داده‌اند.

نسخه‌ی دمو روی Hugging Face Space در دسترس است، اما برای عملکرد حرفه‌ای بهتر است محلی اجرا شود.

LivePortrait

نصب: conda create -n liveportrait python=3.8 + نصب dependencyها.

اجرا: اسکریپت demo برای تولید ویدیو.

ویژگی‌ها: سرعت بالا، پشتیبانی از حیوانات.

AniPortrait

نصب: pip install -r requirements.txt

اجرا: CLI یا Gradio.

ویژگی‌ها: انیمیشن پرتره بر اساس صدا (Audio-Driven).

FSRT

نصب: نیاز به PyTorch + face-alignment.

اجرا: اسکریپت‌های train و eval.

ویژگی‌ها: CVPR 2024، Transformer-based.

scaleway/frontalization

نصب: PyTorch + NVIDIA DALI.

اجرا: اسکریپت‌های آموزش/ارزیابی موجود.

ویژگی‌ها: GAN برای frontalization.

FFWM

نصب: bash setup.sh (PyTorch 1.5 توصیه می‌شود).

اجرا: اسکریپت training و evaluation.

ویژگی‌ها: warp-based frontalization.

نتایج

در این بخش تصاویر خروجی، جدول امتیازها و متریک‌ها (FID, SSIM, FPS و غیره) قرار داده خواهد شد.

نتیجه‌گیری

مدل‌های AniPortrait و LivePortrait برای کاربردهای تعاملی/سینماتیک مناسب‌تر هستند.

FSRT دقت بالایی در انتقال حالت‌ها دارد.

مدل‌های GAN مانند scaleway و FFWM در Frontalization کلاسیک عملکرد خوبی دارند.

FacePoke ابزاری ساده و تعاملی برای دمو و نمایش زنده است.

منابع و استناد

FacePoke – jbilcke-hf

LivePortrait – KwaiVGI

AniPortrait – Zejun-Yang

FSRT – andrerochow

scaleway/frontalization

FFWM – csyxwei
