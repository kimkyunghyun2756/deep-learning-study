## 역전파 수식 유도 정리
# 🔄 역전파 수식 유도

## ✅ 목표
다음 연산에 대해 각 변수에 대한 **기울기(미분값)** 을 수식으로 유도한다.

\[
z = (wx + b)^2
\]

---

## 📌 변수 정의

| 변수 | 설명 |
|------|------|
| \( x \) | 입력값 (예: 2.0) |
| \( w \) | 가중치 (예: 3.0) |
| \( b \) | 편향 (예: 1.0) |
| \( y \) | \( y = wx + b \) |
| \( z \) | \( z = y^2 \) |

---

## 🧮 수식 전개

1. 중간값 정의:

\[
y = wx + b
\]

\[
z = y^2
\]

---

## 📐 미분 계산 (Chain Rule)

\[
\frac{dz}{dy} = 2y
\]

\[
\frac{dy}{dx} = w,\quad \frac{dy}{dw} = x,\quad \frac{dy}{db} = 1
\]

→ Chain Rule 적용:

\[
\frac{dz}{dx} = \frac{dz}{dy} \cdot \frac{dy}{dx} = 2y \cdot w
\]

\[
\frac{dz}{dw} = \frac{dz}{dy} \cdot \frac{dy}{dw} = 2y \cdot x
\]

\[
\frac{dz}{db} = \frac{dz}{dy} \cdot \frac{dy}{db} = 2y \cdot 1 = 2y
\]

---

## 🧠 예제 값 대입 (x = 2, w = 3, b = 1)

\[
y = wx + b = 3 \cdot 2 + 1 = 7
\]

\[
\frac{dz}{dx} = 2 \cdot 7 \cdot 3 = 42
\]

\[
\frac{dz}{dw} = 2 \cdot 7 \cdot 2 = 28
\]

\[
\frac{dz}{db} = 2 \cdot 7 = 14
\]

---

## ✅ 결론

- 수식 유도를 통해 PyTorch가 `.backward()` 호출 시 어떻게 그래디언트를 계산하는지 직접 확인했다.
- Autograd는 이 과정을 **자동으로 처리**해준다.
