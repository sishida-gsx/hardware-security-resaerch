---
layout: default
title: "Docker Kali for penetration testing"
date: 2021-09-29 11:39:30 +0900
categories: penetration
---

# Installing Docker kali

## Pull

{% highlight ruby %}
$ docker pull kalilinux/kali-rolling
{% endhighlight %}

## Run a container and login

{% highlight ruby %}
docker run -itd --rm kalilinux/kali-rolling
docker exec -it {CONTAINER_ID} /bin/bash
{% endhighlight %}



