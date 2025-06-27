---
layout: post
title: Test_Hello
---

### This is a test post

If you're reading this, Jekyll is working!

## 🧩 Question

Write a function to check if a string is a palindrome.

<details>
<summary>💡 Click to reveal the answer</summary>

### ✅ Solution

Use two-pointer technique:

```python
def is_palindrome(s):
    return s == s[::-1]
