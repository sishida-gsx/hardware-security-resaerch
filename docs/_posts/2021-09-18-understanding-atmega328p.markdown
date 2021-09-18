---
layout: default
title: "Understanding ATmega328P"
date: 2021-09-18 14:39:30 +0900
categories: hardware security
---

# Observe assmbly code

Move to the following folder.

{% highlight ruby %}
~/P/s/a/led-blink ❯❯❯ pwd
{your parent dir}/security-resaerch.io/arduino-nano/led-blink
~/P/s/a/led-blink ❯❯❯
{% endhighlight %}

Run make

{% highlight ruby %}
make
{% endhighlight %}

This should give you files like

{% highlight ruby %}
~/P/s/a/led-blink ❯❯❯ ll
total 48
-rw-r--r--  1 gsx  staff   4.6K  9 17 12:17 Makefile
-rw-r--r--  1 gsx  staff   391B  9 17 11:55 main.c
-rwxr-xr-x  1 gsx  staff   6.7K  9 18 12:01 main.elf
-rw-r--r--  1 gsx  staff   508B  9 18 12:01 main.hex
~/P/s/a/led-blink ❯❯❯
{% endhighlight %}

Then, run objdump for avr!

{% highlight ruby %}
~/P/s/a/led-blink ❯❯❯ avr-objdump -S main.elf

main.elf:     file format elf32-avr


Disassembly of section .text:

00000000 <__vectors>:
   0:	0c 94 34 00 	jmp	0x68	; 0x68 <__ctors_end>
   4:	0c 94 3e 00 	jmp	0x7c	; 0x7c <__bad_interrupt>
   8:	0c 94 3e 00 	jmp	0x7c	; 0x7c <__bad_interrupt>
   c:	0c 94 3e 00 	jmp	0x7c	; 0x7c <__bad_interrupt>
{% endhighlight %}


{% highlight ruby %}
00000080 <main>:
  80:   20 9a           sbi     0x04, 0 ; 4
  82:   28 9a           sbi     0x05, 0 ; 5
  84:   2f ef           ldi     r18, 0xFF       ; 255
  86:   89 e6           ldi     r24, 0x69       ; 105
  88:   98 e1           ldi     r25, 0x18       ; 24
  8a:   21 50           subi    r18, 0x01       ; 1
  8c:   80 40           sbci    r24, 0x00       ; 0
  8e:   90 40           sbci    r25, 0x00       ; 0
{% endhighlight %}

