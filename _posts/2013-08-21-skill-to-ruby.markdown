---
layout: post
title:  "Ruby 笔记(一)"
categories: skill
---

ruby 快速排序和冒泡排序
-
###快速排序
快速排序是二叉查找树（二叉查找树）的一个空间优化版本!
{% highlight ruby %}
def sort(array)
	return array if array.size < 2
	left,right = array[1..-1].partition{|y| y<= array.first}
	sort(left)+[array.first]+sort(right)
	#puts new_arr.inspect
end
{% endhighlight %}
partition 是把一个数据按照定义规格分成两个数组