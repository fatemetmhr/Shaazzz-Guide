--- 
hide:
  - footer
comments: true
---
# مقدمه

در این بخش ما قصد داریم ابزار های مهمی رو برای تحلیل زمان اجرای برنامه مان ارائه بدهیم که در تمام مدت دوران برنامه نویسی نیاز خواهند شد. داشتن فهم عمیق از این مباحث ضروری است زیرا تمامی این مباحث در آینده از بخش های جدایی ناپذیر دروس خواهند بود.

###زمان اجرا
می توان برای هر برنامه تابعی به صورت$T$ ارائه داد که بیانگر تعداد عملیات های برنامه مان باشد بر حسب ورودی های داده شده باشد. به عنوان مثال، در مورد کد زیر

```cpp linenums="1"

int sum = 0;
for (int i = 0; i < n; i++) {
    sum += i;
}
```

می توان گفت
$T(n)=3n+3$
به این شکل به عنوان مثال یک تعریف $sum$، یک تعریف $i$، 
$n+1$
بار مقایسه با $n$، 
$n$
بار جمع $i$ با 1 و 
$n$
بار جمع با $sum$ داریم. 

همانطور که می بینید، به دست آوردن مقدار دقیق $T$ کار آسانی نیست و به همین دلیل دانشمندان علوم کامپیوتر تصمیم به محاسبه تقریبی این تابع گرفتند. به عنوان مثال تابعی مانند
$5n^3 + 10n^2 - 3n + 7$
را می توان به صورت
$5n^3$
درنظر گرفت، زیرا بقیه عبارات آن با بزرگ شدن مقدار $n$ تأثیر زیادی روی زمان اجرا ندارند و به همین دلیل می توان برای تقریب آنها را در نظر نگرفت. علاوه بر این خود این تابع را نیز می توان به صورت
$n^3$
درنظر گرفت زیرا به مرور زمان دانشمندان علوم کامپیوتر توانستند با زیاد کردن تعداد کامپیوتر ها ضریب را بی اثر کنند و معمولاً نیز در کد هایی که می زنیم ضرایب آنقدری بزرگ نیستند که بخواهند نقش تعیین کننده ای در پذیرفته شدن کد ما داشته باشند. بنابراین می توان این تابع را به سادگی به صورت
$n^3$
درنظر گرفت و از جزئیات آن رها شد.

در ادامه با با سه معیار ارزشمند تقریب زمان اجرا آشنا می شویم.

#### تحلیل زمان با $O$

یکی از اصلی ترین نماد ها برای تحلیل زمان اجرا علامت O بزرگ است. این نماد به عنوان یک کران بالا برای توابع ما عمل می کند. فلسفه این تابع به این شکل است که فقط تقریب را برای متغیر های بزرگ درنظر می گیرد و همچنین از ضریب صرف نظر می کند، یا به طور دقیق می گوییم تابع $f$ از $O(g)$ است اگر و فقط اگر:

$$\exists n_0, c>0[\forall n > n_0[f(n) < cg(n)]]$$

به عنوان مثال برای
$f(n) = n^5$
و
$g(n) = 5n^3 + 10n^2 - 3n + 7$

داریم
$g \in O(f)$
زیرا می توان
$n_0$ را
$100$
و
$c$
را $6$ بگیریم و بدیهتاً درستی را چک کنیم. بنابراین نماد $O$ به خوبی فلسفه ما را پیاده می کند و می توانیم از آن به عنوان یک معیار عالی برای محاسبه کران بالا استفاده کنیم.

#### تحلیل زمان با $\Omega$

این تابع نیز حکم کران پایین برای توابع ما را دارد، و به نوعی برعکس تابع اردر است، بنابراین به توضیح دقیق ریاضی آن اکتفا می کنیم و از توضیحات اضافه خودداری می کنیم.

$$f \in \Omega(g) \iff \exists n_0, c>0[\forall n > n_0[f(n) > cg(n)]]$$

#### تحلیل زمان با $\theta$

ما در این تابع قصد داریم توابعی که رشد یکسانی دارند را دسته بندی کنیم، و به نوعی تقریبی دقیق تر برای آن ارائه دهیم. عملاً اگر $O$ را $\leq$ و $\Omega$ را $\geq$ بگیریم، $\Theta$ حکم $=$ را دارد. عملاً داریم

$$f \in \Theta(g) \iff f \in O(g) \& f \in \Omega(g)$$

دقت کنید به عنوان مثال
$3n \in O(n^2)$
و
$7n^3 \in \Omega(n^2)$
ولی
$3n \notin \Theta(n^2)$
و
$7n^3 \notin \Theta(n^2)$

در حالی که
$5n^2 + 3n + lg(n) \in \Theta(n^2)$.

!!! danger "قضایای مهم"
    قضایای زیر از قضایای مهم تحلیل اردر هستند که اثبات آنها را به شما واگذار می کنیم.

    1. $f \in O(g) \iff g \in \Omega(f)$
    2. $f \in O(g) \implies f+g \in O(g), f+g \in \Omega(g), f+g \in \Theta(g)$

