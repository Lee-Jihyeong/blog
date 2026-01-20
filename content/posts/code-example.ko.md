---
title: "코드 하이라이팅 예시"
date: 2024-01-20T10:00:00+09:00
draft: false
description: "코드 하이라이팅 스타일을 확인할 수 있는 예시 포스트"
tags: ["코드", "예시", "hugo"]
categories: ["Dev"]
author: "LEE JIHYEONG"
toc: true
show_reading_time: true
---

## 개선된 코드 하이라이팅

이 포스트는 개선된 코드 하이라이팅 스타일을 보여줍니다.

### JavaScript 예시

```javascript
// GitHub 스타일 하이라이팅
function greet(name) {
  console.log(`Hello, ${name}!`);
  return `Welcome to ${name}'s blog`;
}

const user = "LEE JIHYEONG";
greet(user);
```

### Python 예시

```python
# Python 코드 예시
def calculate_sum(numbers):
    """숫자 리스트의 합을 계산합니다."""
    total = 0
    for num in numbers:
        total += num
    return total

numbers = [1, 2, 3, 4, 5]
result = calculate_sum(numbers)
print(f"합계: {result}")
```

### HTML 예시

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>블로그 예시</title>
</head>
<body>
    <h1>안녕하세요!</h1>
    <p>이것은 HTML 예시입니다.</p>
</body>
</html>
```

### CSS 예시

```css
/* CSS 스타일 예시 */
.blog-post {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  line-height: 1.6;
}

.blog-post h1 {
  color: #333;
  font-size: 2rem;
  margin-bottom: 1rem;
}
```

## 개선 사항

- ✅ **GitHub 스타일** 하이라이팅 적용
- ✅ **라인 번호** 자동 표시
- ✅ 더 읽기 쉬운 코드 블록

이제 코드가 더 예쁘게 표시됩니다!
