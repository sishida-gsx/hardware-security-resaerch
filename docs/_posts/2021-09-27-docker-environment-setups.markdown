---
layout: default
title: "Docker Environment Setups"
date: 2021-09-27 14:39:30 +0900
categories: hardware security, docker
---

# Docker containers for development and debug

## Why docker?

Developing and debugging today requires more than just one environment.
Docker simplifies workflows.

## Build docker image

{% highlight ruby %}
~/P/s/docker ❯❯❯ pwd
{your parent dir}/security-resaerch.io/docker
~/P/s/docker ❯❯❯
{% endhighlight %}

Simply run 

{% highlight ruby %}
~/P/s/docker ❯❯❯ ./build.sh
{% endhighlight %}

## Run and login to container

Move to a directory where you want to work.

{% highlight ruby %}
$ docker run --rm -v $PWD:/pwd --cap-add=SYS_PTRACE --security-opt seccomp=unconfined -p 5555:5555 -i ubuntu18:ctf
{% endhighlight %}

After running the command above, the process becomes pending.

![]({{site.baseurl}}/images/pending-terminal.png)

Leave it as is.

Open another terminal as a tab or window of your choice.

{% highlight ruby %}
$ docker ps
CONTAINER ID    IMAGE           ...
1cc5488da0c2    ubuntu18:ctf    ...
{% endhighlight %}

Then, run the following.

{% highlight ruby %}
$ docker exec -it {CONTAINER ID} /bin/bash
{% endhighlight %}

Now, you should be able to login into the container.

In order to see the working folder, run

{% highlight ruby %}
cd /pwd/ 
{% endhighlight %}

## How to work with this environment

Write code with the host computer, execute and debug in the container!

