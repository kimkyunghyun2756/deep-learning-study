# 🧠 간단한 신경망 구조

## ✅ 목표
PyTorch의 `nn.Module`을 사용해 다음을 구현한다:

- 입력층 (Input Layer)
- 은닉층 (Hidden Layer)
- 출력층 (Output Layer)

---

## 🧱 기본 구성 요소

| 구성 요소 | 설명 |
|-----------|------|
| `nn.Linear(in_features, out_features)` | 선형 계층 (fully connected layer) |
| `torch.relu()` | 비선형 활성화 함수 |
| `forward()` | 입력 → 출력 연산 정의 함수 |
| `model(x)` | forward 호출 방식 (권장) |

---

## 🧠 신경망 구조 예시

- 입력: 2차원 텐서 (예: `[x1, x2]`)
- 은닉층: 3개 노드
- 출력층: 1개 노드

```python
Input (2) → Hidden (3) → Output (1)

---

## 🔧 코드 구성 요소 요약

| 구성 요소 | 설명 |
|-----------|------|
| `__init__()` | 신경망 계층(Linear 등)을 정의하는 초기화 메서드 |
| `forward()` | 입력 데이터를 받아 신경망을 통과시키는 흐름(연산)을 정의 |
| `model(x)` | 모델 객체를 함수처럼 호출하면 내부적으로 `forward()` 호출됨 |

---

## 📌 모델 관련 주요 메서드

| 메서드 / 속성 | 설명 |
|----------------|------|
| `model.parameters()` | 학습 가능한 모든 파라미터(weight, bias 등)를 반환 |
| `model.eval()` | 평가 모드 전환 (예: Dropout, BatchNorm이 비활성화됨) |
| `model.train()` | 학습 모드로 다시 전환 (기본값) |

---

## ✅ 예시 코드 흐름 요약

```python
model = SimpleNN()              # 모델 생성
output = model(x_input)         # forward() 자동 호출
params = list(model.parameters())  # 파라미터 조회
model.eval()                    # 평가 모드
model.train()                   # 학습 모드 복귀
