# Day 10 — 시각화 컴포넌트 구현 (Issue #9)

## Why
- 통계 결과는 시각적으로 전달되어야 한다.

## What
- 히스토그램, 박스플롯, 산점도 컴포넌트를 구현했다.

## How
- matplotlib/seaborn을 사용하고 CI용 `Agg` 백엔드를 지정했다.
- figure close를 명시해 메모리 누수를 방지했다.

## 핵심
- headless 환경 백엔드 설정을 먼저 고정해야 테스트가 안정적이다.
