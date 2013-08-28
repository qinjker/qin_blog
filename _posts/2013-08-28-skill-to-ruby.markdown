---
layout: post
title:  "Ruby 笔记(二)"
categories: skill
---
ruby 对象模型
-
*在循环中创建类 是不是定义了多个类？
>不会定义多个类。class关键字更像是一个作用域操作符而不是类的声明语句，核心任务就是把你带到类的上下文，让你可以在其中定义方法！
*打开类带来的问题
1. 猴子补丁－理解为你替换了基本类的原有方法。例如数组替换。(ruby本身replace方法是替换一个整个数组)
{% highlight ruby %}
	class Array
		def	replace_element(from,to)
			each_with_index do |e,i|
				self[i] == to if e == from
			end
		end
	end
{% endhighlight %}
*为什么同一个类的对象共享同样的方法，但不共享实例变量
>一个类的实例变量存在于对象本身，而一个对象的方法存在于对象自身的类
{% highlight ruby %}
 class Aa
 	def	my_method()
 		@v = 1
 		puts "nihao"
 	end
 end
a = Aa.new
puts a.my_method # nihao
puts a.instance_variables #[:@v1]
puts Aa.instance_variables #不输出
puts Aa.methods.grep /my/ #不输出
puts "-----"
puts a.methods.grep /my/ #[:my_method]
puts String.instance_methods == "abc".methods # true
puts String.methods == "adv".methods #false
{% endhighlight %}