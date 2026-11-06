# Sprint 2 Retrospective — 고급 통계 및 시각화

## STAR
- **Situation**: Week 2 이슈 #7~#11, 마일스톤 due 2026-11-20
- **Task**: 가설검정, 회귀, 시각화, 노트북, 문서 완료
- **Action**: scipy/statsmodels 조합과 headless 시각화 파이프라인 적용
- **Result**: 분석부터 시각화까지 end-to-end 예제 확보

## Why What How
- **Why**: 통계 결과를 해석하고 전달할 도구가 필요했다.
- **What**: 가설검정, 회귀, 시각화, 노트북, 문서를 제공했다.
- **How**: 효과 크기, 진단, Agg 백엔드, 실행 가능한 노트북으로 품질을 관리했다.

## Keep
- 효과 크기 동시 반환
- headless 백엔드 고정
- Restart & Run All 검증

## Problem
- 모델 가정 문서가 분산됨
- 시각화 메모리 관리가 컴포넌트마다 다름

## Try
- 모델 카드 템플릿 도입
- 공통 figure lifecycle 유틸 추가
