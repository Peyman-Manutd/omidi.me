---
layout: post
title:  "آموزش نصب فریموورک لاراول"
date:   2016-08-13
urll: "getting-started-with-laravel"
excerpt: "قبل از استارت کار با لاراول، اول اینو بگم که از سه روش مختلف میشه لاراول رو روی سیستم هامون نصب کنیم. دو روش اول قابل اجرا روی مک ، لینوکس و ویندوز هست و روش سوم فقط مخصوص کاربران  مک هست که چند ماه پیش منتشر شد. در هر سه روش نیاز به نصب Composer داریم. "
tags: Laravel Composer PHP
comments: true
---

سلام. راستش خیلی وقت بود که میخواستم بلاگم رو راه بندازم ولی متاسفانه زمان اجازه نمیداد. هدف اصلی من برای درست کردن بلاگ اینه که بتونم تجربه هام رو در زمینه برنامه نویسی در اختیار بقیه بگزارم.


خوشحال میشم نظرهاتون رو از طریق [ایمیل](mailto:{{ site.email }} "peyman@omidi.me") یا کامنت زیر هر پست بم بگید. 😊 

<br/>

خب قبل از استارت کار با لاراول، اول اینو بگم که از سه روش مختلف میشه لاراول رو روی سیستم هامون نصب کنیم. دو روش اول قابل اجرا روی `مک` ، `لینوکس` و `ویندوز` هست و روش سوم فقط مخصوص کاربران  مک هست که چند ماه پیش منتشر شد. در هر سه روش نیاز به نصب [Composer](https://getcomposer.org) داریم. 

<br/>

### توضیحاتی در مورد Composer

Composer یک مدیریت کننده نیازمندی ها (Dependency Manager) برای پکیج های PHP هست. کاری که [Composer](https://getcomposer.org) برای ما انجام میده اینه که مجموعه ای از پکیج های PHP رو در اختیار ما میزاره. برای مثال با استفاده از این پکیج ها، دیگه احتیاج به نوشتن کدهای Validation، Authentication و … که زمان زیادی از ما میگیره نداریم.
برای نمونه [Packagist](https://packagist.org) سایتی هست که میتونین پکیج های مورد نظرتون رو به صورت دستی دانلود کنید.

<br/>

### نصب [Composer در Linux | OSX :](https://getcomposer.org/doc/00-intro.md) 

در ترمینال دستور زیر را برای نصب [Composer](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx) اجرا کنید.

{% highlight html %}
{% raw %}
    Curl -sS http://getcomposer.org/installer | php
{% endraw %}
{% endhighlight %}

چون Composer را بصورت Global میخوایم استفاده کنیم، دستور زیر رو اجرا میکنیم.

{% highlight html %}
{% raw %}
    mv composer.phar /usr/local/bin/composer
{% endraw %}
{% endhighlight %}

کاری که این دستور انجام میده اینه که بجای استفاده از دستور `php composer.phar` به صورت مختصر از دستور `composer` استفاده کنیم.

برای اطمینان از نصب، دستور `composer` را در ترمینال اجرا کنید.

<br/>

### نصب [Composer در ویندوز:](https://getcomposer.org/doc/00-intro.md#installation-windows)

راحتترین و سریعترین راه برای نصب composer، دانلود و نصب آخرین ورژن منتشر شده هست که میتوانید از [اینجا](https://getcomposer.org/Composer-Setup.exe) دانلود کنید.

<br/>

خب حالا برای ساخت پروژه در لاراول، ابتدا در دایرکتوری `htdocs` یا `www`، یک دایرکتوری جدید با نام دلخواه مثلا laravel ایجاد می کنیم. حالا در ترمینال یا `cmd` وارد این دایرکتوری که ساختیم میشیم و این دستور را اجرا میکنیم

{% highlight html %}
{% raw %}
    composer create-project laravel/laravel projectName
{% endraw %}
{% endhighlight %}

بجای `projectName` هر اسمی که میخواید میتونین بنویسین.
بعد از اجرای دستور بالا، منتظر میشیم تا پکیج دانلود بشه.

بعد از تموم شدن مراحل دانلود پکیج لاراوا، لازمه که permission نوشتن (write) رو به فولدر `storage` بدیم. برای اینکار اول در ترمینال یا `cmd` به دایرکتوری laravel، تغییر مسیر میدیم و این دو دستور رو اجرا میکنیم 

{% highlight html %}
{% raw %}
    sudo chmod -R 755 projectName
    chmod -R o+w projectName/storage
{% endraw %}
{% endhighlight %}

برای اجرای پروژه، در مرورگرمون وارد این آدرس میشیم : `localhost/laravel/projectName/public`

در صورتی که مراحل رو درست رفته باشید، باید این صفحه رو ببینید 


<figure>
    <img src="/assets/img/posts-images/blog/getting-started-with-laravel/laravel.png" alt="آموزش نصب لاراول">
</figure>
<br/>

همونطور که میبینید برای دسترسی و اجرای `Homepage` چه مسیر طولانی رو توی `address bar` باید وارد کنیم.

در آموزش بعدی، مراحل نصب لاراول با استفاده از [Laravel Homestead](https://laravel.com/docs/5.2/homestead) بررسی میکنیم که کار با لاراول رو خیلی راحت میکنه. برای مثال میتونیم به راحتی هر url که میخوایم، مثلا `laravel.dev` رو برای پروژمون ست کنیم و از شر این آدرس طولانی و زشت راحت بشیم 😁

<br/>

موفق باشید 👍