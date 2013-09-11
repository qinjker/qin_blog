---
layout: post
title:  "Ruby 笔记(三)"
categories: skill
---
ruby 象棋中A将军和B将军不能碰头情况
－
*解题思路
>象棋盘中将军能移动的格子就是田字格式(3*3)
###遍历A将军的位置
####遍历B将军的位置
######判断A,B的位置组合是否满足要求
######如果满足则输出
*ruby 代码如下
{% highlight ruby %}
	1.upto 9 do |i|
		1.upto 9 do |j|
			if i%3 != j%3
				puts  "i=#{i}:j=#{j}"
			end
		end
	end
{% endhighlight %}