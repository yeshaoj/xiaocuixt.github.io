---
layout: post
title:  "rails中super理解"
date:   2016-07-21 12:30:00
categories: rails
comments: true
---

super是和ruby中继承分不开的,super代表父级那层的与自己同名的method.

1.不带参数

{% highlight ruby %}
class Parent
  def say
     puts "I am a parent"
  end
end
class Son < Parent
   def say
      puts "I am a son"
      super
   end
end
Parent.new.say   =>  "I am a parent"
Son.new.say
   =>  "I am a son"
   => "I am a parent"
{% endhighlight %}

这里super执行了，父级类中的相同名称的方法。

2.带参数

{% highlight ruby %}
class Parent
  def say(name)
     puts "#{name} is a parent"
  end
end
class Son < Parent
   def say(name)
      puts "#{name} is a son"
      super(name)
   end
end
Parent.new.say("Tom")   =>  "Tom is parent"
Son.new.say("Jim")
   =>  "Jim is a son"
   =>  "Jim is a parent"
{% endhighlight %}

参考：

<a href="http://bbs.chinaunix.net/thread-1278613-1-1.html">http://bbs.chinaunix.net/thread-1278613-1-1.html</a>

<a href="http://rubylearning.com/satishtalim/ruby_overriding_methods.html">http://rubylearning.com/satishtalim/ruby_overriding_methods.html</a>