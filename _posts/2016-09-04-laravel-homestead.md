---
layout: post
title:  "راه اندازی فریموورک لاراول با استفاده از Homestead"
date:   2016-09-04
description: "Laravel Homestead یک pre-package از Vagrant Box هست که محیط توسعه ای در اختیار ما میگذاره که احتیاجی به نصب PHP، وب سرور یا هر نوع نرم افزار مربوط به سرور روی سیستممون نداریم. Vagrant به عنوان یک Virtual Machine کار میکنه که درون اون پکیجی از نرم افزار های مورد نیاز قرار دار "
urll: "laravel-homestead"
excerpt: "Laravel Homestead یک pre-package از Vagrant Box هست که محیط توسعه ای در اختیار ما میگذاره که احتیاجی به نصب PHP، وب سرور یا هر نوع نرم افزار مربوط به سرور روی سیستممون نداریم. Vagrant به عنوان یک Virtual Machine کار میکنه که درون اون پکیجی از نرم افزار های مورد نیاز قرار داره "
tags: Laravel Homestead Vagrant Composer PHP
keywords: لاراول , فریموورک لاراول , آموزش نصب لاراول , لاراول Homestead, Laravel Homestead, Vagrant, کامپوزر, نصب Composer, Composer, PHP, Laravel, Packagist, Sublime Text, VMWare, VirtualBox, SSH Key, پورت فورواردینگ, Forwarding Ports, پیمان امیدی, Peyman Omidi,
comments: true
---

در <a href="http://omidi.me/blog/getting-started-with-laravel/" target="_blank">پست قبلی</a> نحوه نصب و راه اندازی فریموورک لاراول رو از طریق نصب <a href="https://getcomposer.org/" target="_blank">Composer</a> و اجرای اون روی نرم افزار های شبیه ساز سرور مثل `Wamp Server` و `Xampp` و `Mamp` و ... دیدیم.
در این پست آموزش راه اندازی فریموورک لاراول رو بوسیله <a href="https://laravel.com/docs/5.3/homestead" target="_blank">Homestead</a> یاد میگیریم. قبل از ادامه خوندن این پست، مطمئن بشین که `Composer` روی سیستمتون نصب هست.

آموزش نصب `composer` رو میتونین از <a href="http://omidi.me/blog/getting-started-with-laravel/" target="_blank">اینجا</a> بخونید.

برای کاربرانی که از ویندوز استفاده می کنن پیشنهاد میکنم که <a href="https://git-for-windows.github.io" target="_blank">Git Bash</a> رو نصب کنن. `Git Bash` یه Command Line هست که به ما اجازه میده دستورات `Unix` رو اجرا کنیم.

<br/>

## Laravel Homestead

خب برای شروع یه توضیح بدم که <a href="https://laravel.com/docs/5.3/homestead" target="_blank">Laravel Homestead</a> چیه. 
`Laravel Homestead` یک `pre-package` از <a href="https://www.vagrantup.com" target="_blank">Vagrant Box</a> هست که محیط توسعه ای در اختیار ما میگذاره که احتیاجی به نصب `PHP`، وب سرور یا هر نوع نرم افزار مربوط به سرور روی سیستممون نداریم. `Vagrant` به عنوان یک `Virtual Machine` کار میکنه که درون اون پکیجی از نرم افزار های مورد نیاز قرار داره. لیستی از نرم افزار ها که در این پکیج قرار داره:

* Ubuntu 16.04 
* Git
* PHP 7.0 
* Nginx
* MySQL
* MariaDB
* SQlite3
* Postgres
* Composer
* Node (PM2, Bower, Grunt and Gulp)
* Redis
* Memcached
* Beanstalkd

Vagrant Box رو میتونین از <a href="https://www.vagrantup.com/downloads.html" target="_blank">اینجا</a> دانلود کنید.

قبل از اجرای `Homestead` نیاز داریم که حتما <a href="https://www.virtualbox.org/wiki/Downloads" target="_blank">VirtualBox</a> یا <a href="http://www.vmware.com/" target="_blank">VMWare</a> نصب کنیم.

بعد از نصب `Virtual Box/VMWare` و `Vagrant`، باید پکیچ <a href="https://packagist.org/packages/laravel/homestead" target="_blank">Laravel/Homestead</a> رو به `Vagrant Box` اضافه کنیم. اول وارد `home directory` میشیم و این دستور رو اجرا میکنیم.

{% highlight html %}
{% raw %}
    vagrant box add laravel/homestead
{% endraw %}
{% endhighlight %}

توجه داشته باشید که این پکیج حجم بالایی داره (در حدود ۱ GB) و ممکنه با توجه به سرعت اینترنت شما، زمان زیادی طول بکشه.
{: .notice}

بعد از تموم شدن مراحل نصب، ما `Vagrant` و `VirtualBox/VMWare` رو روی سیستممون داریم. حالا کاری که باید بکنیم اینه که یه دایرکتوری جدید برای `Homestead` ایجاد کنیم. برای مثال من در `home directory`، دایرکتوری جدیدی با نام `www` ایجاد کردم و بعد از وارد شدن به این دایرکتوری، دستور پایین رو برای نصب `Homestead` اجرا میکنیم

{% highlight html %}
{% raw %}
    git clone https://github.com/laravel/homestead.git Homestead
{% endraw %}
{% endhighlight %}

همچنین درون دایرکتوری `www` یک دایرکتوری جدید مثلا با نام `sites` ایجاد میکنیم که تمام سایت هایی که ایجاد میکنیم در اینجا قرار داره.
بعد از اینکه دستور بالا رو اجرا کردیم، در دایرکتوری `Homestead`، این دستور رو اجرا میکنیم

{% highlight html %}
{% raw %}
    bash init.sh
{% endraw %}
{% endhighlight %}

با اجرای این دستور، دایرکتوری جدیدی با نام `homestead.` در `home directory` سیستمتون ساخته میشه. درون این دایرکتوری، فایلی به نام `Homestead.yaml` وجود داره که باید اونو ادیت کنیم.
برای باز کردن چنین فایلایی در Command Line چندین راه وجود داره،
یکی از راه های مرسوم استفاده از دستور `nano` هست.
روش بهتر و کاربردی تر باز کردن فایل در کد ادیتور هست. مثلا برای باز کردن فایل بوسیله کد ادیتور <a href="https://www.sublimetext.com" target="_blank">Sublime Text</a>، با استفاده از دستور پایین میتونین دستور `sublime` رو به Command Line سیستمتون اضافه کنید

{% highlight html %}
{% raw %}
ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/sublime
{% endraw %}
{% endhighlight %}

حالا میتونیم با استفاده از این دستور، فایل `Homestead.yaml` رو درون `Sublime Text` باز کنیم (قبل از اجرای دستور وارد دایرکتوری `homestead.` بشید)

{% highlight html %}
{% raw %}
    sublime Homestead.yaml
{% endraw %}
{% endhighlight %}

بعد از باز کردن فایل، قسمت `folders` و `sites` رو مثل عکس پایین تغییر میدیم

<figure>
    <img src="/assets/img/posts-images/blog/laravel-homestead/homestead-yaml.png" alt="Edit Homestead.yaml file" title="Edit Homestead.yaml file" />
</figure>

در صورتی که `SSh Key` ایجاد نکردید، از طریق این دستور میتونید این کار رو انجام بدید

{% highlight html %}
{% raw %}
    ssh-keygen -t rsa -C "you@homestead"
{% endraw %}
{% endhighlight %} 

هنگامی که `SSH Key` ایجاد شد. آدرس کلید رو در قسمت `authorize` قرار بدید.

توجه کنید که در قسمت `folders` حتما دایرکتوری پایین `map` و `to` یکسان باشن و همچنین در قسمت `sites` در `map` آدرس `url` که برای پروژمون استفاده کنیم رو مینویسیم و در `to` آدرس `root` پروژه
{: .notice}

بعد از ذخیره کردن فایل، وارد دایرکتوری `Homestead` در `www` میشیم و این دستور رو اجرا میکنیم و منتظر مشیشم تا `Vagrant Box` اجرا بشه

{% highlight html %}
{% raw %}
    vagrant up
{% endraw %}
{% endhighlight %} 

<br/>

<figure>
    <img src="/assets/img/posts-images/blog/laravel-homestead/vagrant-up.png" alt="Vagrant Up Laravel" title="Vagrant Up Laravel" />
</figure>
<br/>

همونطور که در قسمت `Forwarding Ports` میبینیم، بعد از اجرای `Vagrant` پورت ها تغییر کردن:

* HTTP:        80 => 8000
* HTTPS:        443 => 44300
* MySQL:        3306 => 33060
* PostgresSQL:  5432 => 54320
* SSH/SFTP:     22 => 2222


خب حالا باید `laravel.dev` رو که توی `Homestead.yaml` اضافه کردیم به ip address به اصطلاح `map` کنیم. برای اینکار در ترمینال وارد `home directory` میشیم و این دستور رو اجرا میکنیم

{% highlight html %}
{% raw %}
    sudo vi /etc/hosts/
{% endraw %}
{% endhighlight %}

<br/>

دستور `vi` هم مثل `nano` برای باز کردن این نوع فایل ها از طریق command line هست.
{: .notice}

<br/>

<figure>
    <img src="/assets/img/posts-images/blog/laravel-homestead/map-url-to-ip-address.png" alt="Mapping url to IP Address" title="Mapping url to IP Address" />
</figure>
<br/>

همونطور که در تصویر بالا میبینیم `laravel.dev` رو به ip `127.0.0.1`، `map` میکنیم.

برای ذخیره کردن فایلی که با دستور `vi` باز میکنیم، کلید `Esc` میزنیم و `wq:` رو تایپ و اینتر میکنیم.
{: .notice}

بعد از اینکه ip رو به پروژمون `map` کردیم، وارد مسیر `/www/Homestead/` میشیم و این دستور رو اجرا میکنیم

{% highlight html %}
{% raw %}
    vagrant provision
{% endraw %}
{% endhighlight %}

خب آخرین مرحله قبل از اینکه پروژمون رو ایجاد کنیم، اجرای این دستور هست

{% highlight html %}
{% raw %}
    composer global require "laravel/installer"
{% endraw %}
{% endhighlight %}

با اجرای این دستور، دستور `laravel` بصورت `global` روی سیستم ما قرار میگیره.

خب برای ایجاد پروژه جیدی براحتی میتونیم با استفاده از دستور `laravel new ProjectName` این کار رو انجام بدیم. فقط قبل از اون، وارد دایرکتوری `/www/sites/` میشیم.

{% highlight html %}
{% raw %}
    laravel new laravel
{% endraw %}
{% endhighlight %}

منتظر میشیم تا دانلود پکیج های مورد نیاز تموم بشه. بعد از اون مرورگرومون رو باز میکنیم و `laravel.dev:8000` رو در آدرس بار وارد میکنیم 😍

<figure>
    <img src="/assets/img/posts-images/blog/laravel-homestead/laravel.png" alt="Laravel Homestead up and running" title="Laravel Homestead up and running" />
</figure>

همون طور که میبینیم، نسبت به روش قبل، این روش url بسیار کوتاه تر و به اصطلاح تمیزتری داره.

<br/>

در آموزش بعدی روش آخر راه اندازی فریموورک لاراول رو با استفاده از <a href="https://laravel.com/docs/5.3/valet" target="_blank">Valet</a> بتون میگم که جدیدا معرفی شده و فقط برای کاربران `Mac` هست. جالبی این روش این هست که هیچ احتیاجی به `Vagrant`، `Apache` و `Nginx` نداریم !!! 😳

<br/>

خوشحال میشم نظراتتون رو بخونم. 😊

موفق باشید 👍🏻