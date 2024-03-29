<div dir="rtl" align='right'>

## ادامه ی پردازش زبان طبیعی با یادگیری عمیق

## تبدیل کلمه به بردار
خب دیدی که شبکه های عصبی برای پردازش متن، ابتدا اون ها رو تبدیل به بردار میکنن.  یک روش که دیدی این بود که برای هر کلمه یک شماره اختصاص بدی. دیدی که شبکه عصبی یک لایه Embedding داره که بردارهای ورودی پردازش میکنه و نمایش جدیدی از اونها ارائه میکنه. میتونیم امبدینگ هر چیزی رو بدست بیاریم. مثلا امبدینگ کلمه، جمله، تصویر، صدا، ویدئو ... . مثلا توی Word Embedding، یک بردار میسازی که مشخصات اون کلمه رو بیان میکنه. مثلا میخوایم یک نمایش برداری برای کلمات داشته باشیم، چند تا ویژگی رو در نظر میگیرم:

|کلمه|زنده|شیء|بزرگ|خوردنی|
|-------|----|---|-----|----|
|مرد|1|-1|1|-1|
|پسر|1|-1|-1|-1|
|ماهی|1|-1|-1|1|
|خودکار|-1|1|-1|-1|


توی جدول بالایی یه سری ویژگی مشخص کردیم و برای هر کلمه مقدار اون ویژگی رو تعیین کردیم. اگه کلمه ای اون ویژگی رو داشت مقدارش +1 میشه و اگه نداشت، مقدار اون ویژگی -1 میشه. با این حساب، میتونیم کلمه ی مرد رو با این بردار نمایش بدیم:

مرد=[1,1-,1,-1]

با این بردارها میتونیم تشابه دو کلمه رو با استفاده از ضرب داخلی بدست بیاریم. هر چقدر میزان این ضرب داخلی زیاد بود، یعنی دو کلمه مشابه هستند. مثلا ضرب داخلی کلمه مرد و پسر میشه 2. ضرب داخلی پسر و خودکار میشه صفر. یعنی تشابه مرد و پسر بیشتر از تشابه پسر و خودکار هست!

حتی میشه با این بردارها عملیات ریاضی انجام داد. مثلا اون ها رو از هم کم کرد تا تفاوتشون رو دید. مثلا اگه بردار کلمه مرد رو از پسر کم کنیم، همه ی درایه ها بجز ویژگی بزرگ بودن صفر میشه. یعنی تفاوت مرد و پسر در بزرگ بودنشون هست!

ولی تو جدول بالایی یک نکته ای هست، ضرب داخلی کلمه پسر و ماهی هم میشه 2! یعنی همونقدر که پسر به مرد شبیهه، به ماهی هم شبیهه؟! اینجا دو تا ایراد هست: یکی اینکه تعداد ویژگی های کمی استفاده کردیم، دومی هم اینکه مقدار ویژگی ها رو فقط 1 و -1 در نظر گرفتیم. اگه این دو مورد رو برطرف کنیم، امبدینگ بهتری میتونیم بدست بیاریم.

حالا برای این همه کلمه چطوری امبدینگ ایجاد کنیم؟ امکان نداره که بشینیم تک تک برای هر کلمه، ویژگی هاش رو بنویسیم! پس باید از یه روش یادگیری ماشینی استفاده کنیم. برای اینکه بدونی چطوری این Embedding ها بدست میاد، لینک زیر رو ببین:
[آشنایی بیشتر با Embedding](https://machinelearningmastery.com/what-are-word-embeddings/)

* توی شبکه ی عصبی یک لایه Embedding گذاشتی. از طریق اون لایه، امبدینگ چند تا کلمه دلخواه رو بدست بیار و تشابهشون رو بررسی کن.
* Gensim یک کتابخونه ست که میتونی باهاش Word Embedding بدست بیاری. توی لینک زیر نحوه استفاده ازش اومده. برای مجموعه اخبار روزنامه همشهری، Word Embedding  رو بدست بیار. [آموزش Embedding  با Gensim](https://radimrehurek.com/gensim/models/word2vec.html)
* حالا که Word Embedding رو بدست آوردی، از اون توی شبکه ی عصبی استفاده کن. یعنی بجای اینکه کلمات رو با عدد ایندکسش نشون بدی و وارد شبکه کنی، اونا رو با امبدینگشون نمایش بده و وارد شبکه کن. نتایج رو با حالت قبلی بررسی کن و گزارش بده.
* (اختیاری) پروژه Fasttext توسط فیسبوک توسعه و بصورت متن باز منتشر شده است. این پروژه برای بیش از 157 زبان از جمله فارسی، Word Embedding ارائه کرده است. ابتدا مستندات موجود در سایت این پروژه رو بررسی کن و سپس از امبدینگ موجود در این سایت استفاده کن و مثل تسک قبلی، شبکه رو آموزش بده و نتایج رو مقایسه کن.
[لینک سایت Fasttext](https://fasttext.cc/)

* (اختیاری) برای نمایش امبدینگ های آموزش داده شده، میتونی از این سایت تنسورفلو استفاده کنی:
  [نمایش امبدینگ ها](https://projector.tensorflow.org/)
