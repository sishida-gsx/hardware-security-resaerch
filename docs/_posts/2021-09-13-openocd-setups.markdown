---
layout: default
title: "OpenOCD"
date: 2021-09-13 11:39:30 +0900
categories: hardware security
---

# OpenOCD


## Installing OpenOCD

{% highlight ruby %}
brew install openocd
{% endhighlight %}

Detailed user's guide for OpenOCD is [https://openocd.org/doc/html/index.html](https://openocd.org/doc/html/index.html)

{% highlight ruby %}
git clone https://github.com/openocd-org/openocd.git
{% endhighlight %}

## find config files

for JLink

{% highlight ruby %}
~/P/openocd ❯❯❯ ls tcl/interface/jlink.cfg
tcl/interface/jlink.cfg
~/P/openocd ❯❯❯
{% endhighlight %}

