---
layout: post
title:  "آموزش نصب لاراول Valet"
date:   2016-10-01
description: "احتمالا همه ما وقتی یه پروژه رو بصورت local اجرا میکنیم، دوست داریم از شر localhost نوشتن راحت بشیم و از یه آدرس کوتاه و شیک مثل app.dev یا شبیه این استفاده کنیم."
excerpt: "احتمالا همه ما وقتی یه پروژه رو بصورت local اجرا میکنیم، دوست داریم از شر localhost نوشتن راحت بشیم و از یه آدرس کوتاه و شیک مثل app.dev یا شبیه این استفاده کنیم."
tags: Laravel Valet Homebrew
keywords: لاراول valet, آموزش نصب لارال valet, لاراول ولت, لاراول, اشتراک گذاری, اشتراک گذاری پروژه, استفاده از SSL, نصب PHP7 و MySQL, نصب Homebrew, Laravel Valet, نحوه استفاده از لاراول valet, لاراول Homestead, پیمان امیدی, Peyman Omidi, 
comments: true
---

احتمالا همه ما وقتی یه پروژه رو بصورت local اجرا میکنیم، دوست داریم از شر localhost نوشتن راحت بشیم و از یه آدرس کوتاه و شیک مثل `app.dev` یا شبیه این استفاده کنیم.

این امکان رو ابزارایی مثل <a href="https://www.mamp.info/en/" target="_blank">Mamp</a>، <a href="https://www.vagrantup.com" target="_blank">Vagrant</a> و حتی <a href="http://www.wampserver.com" target="_blank">Wamp</a> در اختیار ما میزاره ولی کمی پیچیده هست، مخصوصا وقتی برای اولین بار باشه که بخوایم اینکار رو انجام بدیم.
مشکل پیچیدگی که این روش ها دارن اینه که همون موقع که پروژمون رو ساختیم نمیتونیم از این نوع آدرس استفاده کنیم و قبلش حتما باید تنظیمات رو بصورت دستی انجام بدیم و میتونه زمان بر باشه.

راه حل خیلی راحت و ساده برای این کار، استفاده از <a href="https://laravel.com/docs/5.2/valet" target="_blank">Laravel Valet</a> هست.

<br/>

# <a href="https://laravel.com/docs/5.2/valet#installation" target="_blank">Laravel Valet</a>

خب برای شروع اول از همه باید `Laravel Valet` رو نصب کنیم.

لاراول valet فقط مخصوص کاربران `Mac` هست و اگر شما کاربر ویندوز هستید میتونید از <a href="https://www.vagrantup.com" target="_blank">Vagrant</a> برای اینکار استفاده کنید و برای هر پروژه، `host file` رو بصورت دستی آپدیت کنید.
{: .notice}


در صورتی که <a href="https://packagist.org/packages/laravel/laravel" target="_blank">پکیج Laravel/Laravel</a> روی سیستم شما نصب نیست، پیشنهاد میکنم اول <a href="http://omidi.me/blog/getting-started-with-laravel/" target="_blank">آموزش نصب لاراول</a> و <a href="http://omidi.me/blog/laravel-homestead/" target="_blank">آموزش نصب لاراول با استفاده از Homestead</a> رو حتما بخونید و لاراول رو روی سیستمتون نصب کنید.
{: .notice}

<br/>

## نصب <a href="http://brew.sh" target="_blank">Homebrew</a>

خب اول از همه ما باید `Homebrew` رو نصب کنیم.
با استفاده از این دستور میتونیم `Homebrew` رو روی سیستممون نصب کنیم.

{% highlight html %}
{% raw %}
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endraw %}
{% endhighlight %}

`Homebrew` در حقیقت یک `Package Manager` برای سیستم عامل `Mac` هست.
{: .notice}


برای اطمینان از نصب `Homebrew`، دستور `brew` رو در ترمینال اجرا میکنیم. اگر مراحل نصل درست انجام شده باشه، لیستی از دستورهای قابل اجرا با `brew` رو میبینیم.


<figure>
    <img src="/assets/img/posts-images/blog/laravel-valet/brew-commands.png" alt="Brew Commands" title="Brew Commands" />
</figure>

<br/>

## نصب PHP7 و MySQL

بعد از نصب `Homebrew`، نوبت به نصب `PHP7` و `MySQL` هست.
برای نصب `PHP7` دستور زیر رو اجرا میکنیم.

{% highlight html %}
{% raw %}
    brew install homebrew/php/php70
{% endraw %}
{% endhighlight %}


موردی که ممکنه حین انجام کار روی پروژه هامون باهاش مواجه بشیم، ارور مربوط به `mcrypt` هست که به دلیل نصب نبودن روی سیستمه.

برای نصب افزونه `mcrypt` این دستور رو اجرا میکنیم.

{% highlight html %}
{% raw %}
    brew install homebrew/php/php70-mcrypt
{% endraw %}
{% endhighlight %}


mcrypt در حقیقت جایگزین دستور `crypt` در `Unix` شده که وظیفه `Encrypt` کردن فایل رو داشت. در واقع mcrypt هم همون کار رو میکنه ولی با الگوریتم های جدیدی مثل `AES`
{: .notice}

در صورتی که دوست دارین لیست افزونه های بیشتری رو برای PHP7 ببینید، از این دستور استفاده کنید.

{% highlight html %}
{% raw %}
    brew search php7
{% endraw %}
{% endhighlight %}


برای نصب `MySQL` هم این دستور رو در ترمینال اجرا میکنیم.

{% highlight html %}
{% raw %}
    brew install mysql
{% endraw %}
{% endhighlight %}

<br/>

خب مرحله بعد نصب Laravel Valet هست که باید از طریق `Composer` اینکار رو انجام بدیم.
شما میتونید آموزش نصب <a href="https://getcomposer.org" target="_blank">Composer</a> رو از <a href="http://omidi.me/blog/getting-started-with-laravel/" target="_blank">اینجا</a> بخونید.

بعد از نصب Composer، از طریق این دستور، <a href="https://packagist.org/packages/laravel/valet" target="_blank">پکیج Laravel/Valet</a> رو دانلود و نصب میکنیم.

{% highlight html %}
{% raw %}
    composer global require laravel/valet=~1.0
{% endraw %}
{% endhighlight %}

بعد از نصب valet بصورت global دستور زیر رو اجرا میکنیم،

{% highlight html %}
{% raw %}
    valet install
{% endraw %}
{% endhighlight %}


خب حالا بعد از نصب valet نیاز داریم یک دایرکتوری مشخص کنیم که همه پروژه هامون که قراره روی valet اجرا بشه در این دایرکتوری قرار داشته باشه.
من به شخصه همونطور که توی دو پست قبل گفتم، در `home directory` یک دایرکتوری `www` دارم که همه پروژهام در اون قرار داره. حالا یک دایرکتوری جدید بنام `valet` در `www` میسازم که همه پروژه هایی که قراره روی valet اجرا بشه، اینجا قرار داشته باشه.

حالا باید این دایرکتوری که برای پروژمون مشخص کردیم رو به valet بشناسونیم یا به اصطلاح این دایرکتوری رو روی valet `پارک` کنیم.
قبل از اجرای دستور پایین باید وارد دایرکتوری مورد نظرمون بشیم.

{% highlight html %}
{% raw %}
    valet park
{% endraw %}
{% endhighlight %}


حالا توی همون دایرکتوری یک پروژه جدید با لاراول به اسم `app` ایجاد میکنیم.
دقت کنید هر اسمی که برای پروژمون تعریف کنیم، به عنوان دامین استفاده میشه.

{% highlight html %}
{% raw %}
    laravel new app
{% endraw %}
{% endhighlight %}


بعد از ایجاد پروژه جدید، وارد مرورگر مشیم و آدرس `app.dev` رو وارد میکنیم.
به همین راحتی 😍


<figure>
    <img src="/assets/img/posts-images/blog/laravel-valet/laravel-valet.png" alt="Laravel Valet" title="Laravel Valet" />
</figure>

<br/>

# استفاده از دامین دیگر

بصورت پیشفرض، valet روی domain extension `.dev` اجرا میشود. در صورتی که بخوایم میتونیم با استفاده از دستور زیر، از domain extension مورد نظرمون استفاده کنیم که برای مثال در این دستور به `.app` تغییر میدیم. شما میتونین بجای `app` از هر کلمه ای استفاده کنید.

{% highlight html %}
{% raw %}
    valet domain app
{% endraw %}
{% endhighlight %}

<br/>

# استفاده از 🔒 SSL

با استفاده از این دستور میتونیم سایت رو از طریق `SSL` اجرا کنیم.

{% highlight html %}
{% raw %}
    valet secure app
{% endraw %}
{% endhighlight %}

که `app` در اینجا نام دایرکتوری پروژمون هست.

برای بازگرداندن به حالت قبل یا استفاده از HTTP میتونیم از این دستور استفاده کنیم.

{% highlight html %}
{% raw %}
    valet unsecure app
{% endraw %}
{% endhighlight %}

<br/>

# <a href="https://laravel.com/docs/5.2/valet#sharing-sites" target="_blank">به اشتراک گذاری پروژه</a>

یکی از قابلیت های فوق العاده valet، امکان اشتراک گذاری پروژه هست.
برای استفاده از این امکان، وارد دایرکتوری پروژمون میشیم و این دستور رو اجرا میکنیم.

{% highlight html %}
{% raw %}
    valet share
{% endraw %}
{% endhighlight %}


<figure>
    <img src="/assets/img/posts-images/blog/laravel-valet/sharing-sites.png" alt="Laravel Valet Sharing Sites" title="Laravel Valet Sharing Sites" />
</figure>


همونطور که در عکس هم میبینیم. در قسمت `forwarding` آدرسی در اختیار ما قرار میگیره که میتونیم این آدرس رو به اشتراک بگذاریم.
فقط با یه دستور ساده بقیه میتونن پروژه ای که بصورت local روی سیستم اجرا شده رو ببینن !!!

واقعا فوق العاده نیست ؟!! 😍