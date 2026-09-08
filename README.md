# 가격 파괴자 — 30초 게임하고 할인쿠폰 받기

가격표를 베어 할인쿠폰을 받는 30초짜리 웹 미니게임. 의존성 없는 단일 HTML 파일(`index.html`)입니다.

## 규칙
- 🏷️ 가격표를 베면 +1, 한 번에 3장 이상 베면 콤보 +2
- 💣 환불폭탄을 베면 −3
- ⏱️ 30초 안에 20장이면 20% 쿠폰, 못 채워도 이메일 등록 시 20% 쿠폰

## 리드 수집
쿠폰 발급 시 아래 필드를 웹훅(Make.com)으로 `application/x-www-form-urlencoded` POST 합니다.

| 필드 | 예시 | 설명 |
|---|---|---|
| `date` | `2026-09-08` | 발급일 (Asia/Seoul) |
| `time` | `21:18:54` | 발급 시각 (Asia/Seoul) |
| `email` | `name@example.com` | 수집 이메일 |
| `code` | `WIN20-A3F9` | 발급된 쿠폰 코드 |
| `score` | `27` | 벤 가격표 수 |
| `cleared` | `true` | 목표 달성 여부 |
| `discount` | `20` | 할인율 |
| `agreedAt` | ISO 8601 (UTC) | 개인정보 수집 동의 시각 |
| `source` | `price-slasher-game` | 유입 구분 |

전송 실패 시 `navigator.sendBeacon`으로 재시도하고, 그래도 실패하면 폼에 오류를 표시합니다.

## 실행
```
open index.html
```
