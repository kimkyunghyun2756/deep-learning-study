## Autograd 개념 정리
# ⚙️ Autograd란?

## ✅ 정의
- Autograd는 PyTorch의 **자동 미분 엔진**이다.
- 텐서에 `requires_grad=True`를 설정하면, **연산 기록을 추적**하고 `.backward()` 호출 시 자동으로 **미분 계산**을 수행한다.

---

## 🔁 작동 원리

1. `requires_grad=True`인 텐서끼리 연산하면 **계산 그래프**가 생성됨
2. `loss.backward()`를 호출하면 **모든 텐서에 대해 chain rule로 미분 계산**
3. 결과는 `.grad` 속성에 자동 저장됨

---

## 📌 주요 속성 및 함수

| 속성/함수 | 설명 |
|-----------|------|
| `requires_grad` | 텐서가 미분 대상인지 여부 설정 |
| `.backward()` | 그래디언트 계산 실행 |
| `.grad` | 계산된 미분값 (기울기) |
| `with torch.no_grad():` | 연산 중 autograd 비활성화 (추론시 사용) |

---

## 🧠 예시

```python
x = torch.tensor([2.0], requires_grad=True)
w = torch.tensor([3.0], requires_grad=True)
b = torch.tensor([1.0], requires_grad=True)

y = w * x + b        # y = 3*2 + 1 = 7
z = y ** 2           # z = 49

z.backward()         # 자동 미분 수행

print(x.grad)        # ∂z/∂x = 2 * y * w = 2 * 7 * 3 = 42
print(w.grad)        # ∂z/∂w = 2 * y * x = 2 * 7 * 2 = 28
print(b.grad)        # ∂z/∂b = 2 * y * 1 = 2 * 7 * 1 = 14

### ✅ 요약
- requires_grad=True → autograd 추적 시작
- backward() 호출 → 그래프 따라 자동 미분 수행
- grad 속성 → 결과 기울기 확인
- torch.no_grad() → 추론 시 autograd 비활성화
- grad.zero_() → 반복 계산 전 초기화 필수
