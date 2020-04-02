---
layout: post
title: Số Fibonacci!
---

# Đề bài
Các số Fibonacci, thường được ký hiệu là F(n) tạo thành một chuỗi, được gọi là chuỗi Fibonacci, sao cho mỗi số là tổng của hai số trước, bắt đầu từ 0 và 1.
Nghĩa là: 
F(0) = 0, F(1) = 1
F(N) = F(N - 1) + F(N - 2), với N > 1.

Cho N, tính F (N).

# Ví dụ

## Ví dụ 1:
Đầu vào: 2

Đầu ra: 1

Giải thích: F(2) = F(1) + F(0) = 1 + 0 = 1.

## Ví dụ 2:
Đầu vào: 3

Đầu ra: 2

Giải thích: F(3) = F(2) + F(1) = 1 + 1 = 2.

# Source code
```
public int fib(int n) {
    switch (n)
    {
        case 0:
          return 0;
        case 1:
          return 1;
        default:
          int[] nums = new int[n + 1];
          nums[0] = 0;
          nums[1] = 1;
          for (int i = 2; i <= n; i++)
          {
              nums[i] = nums[i - 1] + nums[i - 2];
          }
          return nums[n];
    }
}
```
