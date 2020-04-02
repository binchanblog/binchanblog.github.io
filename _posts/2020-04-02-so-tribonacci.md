---
layout: post
title: Số Tribonacci!
---

# Đề bài
Chuỗi Tribonacci được định nghĩa như sau:

T[0] = 0,  T[1] = 1, T[2] = 1 

và T[n+3] = T[n] + T[n+1] + T[n+2] với n> = 0.

Cho n, trả về giá trị của T[n].

# Ví dụ

### Ví dụ 1:

Đầu vào: n = 4

Đầu ra: 4

Giải thích:

T[3] = 0 + 1 + 1 = 2

T[4] = 1 + 1 + 2 = 4

# Source code

{% highlight js %}
public int tribonacci(int n) {
	switch (n)
	{
		case 0:
			return 0;
		case 1:
		case 2:
			return 1;
		default:
			int[] nums = new int[n + 1];
			nums[0] = 0;
			nums[1] = 1;
			nums[2] = 1;

			for (int i = 3; i <= n; i++)
			{
				nums[i] = nums[i - 1] + nums[i - 2] + nums[i - 3];
			}

			return nums[n];
	}
}
{% endhighlight %}
