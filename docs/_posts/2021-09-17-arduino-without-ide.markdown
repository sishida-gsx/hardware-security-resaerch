---
layout: default
title: "Arduino without IDE"
date: 2021-09-17 11:39:30 +0900
categories: hardware security
---

# Arduino NANO without IDE


## Installing Arduino IDE

Download from [https://www.arduino.cc/](https://www.arduino.cc/) install.
This contains not only IDE not also commandline tools, which we want right now.

## Create a symbolic link for AVR tools

avr folder should contain various tools.

{% highlight ruby %}
cd /usr/local
sudo ln -s /Applications/Arduino.app/Contents/Java/hardware/tools/avr avr
{% endhighlight %}

## Set execution path

Run the following or add it to .bashrc/.zshrc file.

{% highlight ruby %}
export PATH=/usr/local/bin:/usr/local/avr/bin:$PATH
{% endhighlight %}

## Install avrdude

{% highlight ruby %}
brew install avrdude
{% endhighlight %}


