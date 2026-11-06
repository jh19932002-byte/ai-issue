# Sprint 1 Retrospective — 데이터 탐색 및 기초 통계

## STAR
- **Situation**: Week 1 이슈 #2~#6, 마일스톤 due 2026-11-13
- **Task**: 프로젝트 구조, 로더, 기초 통계, 정제, 테스트 완료
- **Action**: 구조 고정 후 data validation과 ddof 정책을 명확히 구현
- **Result**: 핵심 통계 함수와 테스트 기반 확보

## Why What How
- **Why**: 재현 가능한 기초 통계 패키지가 필요했다.
- **What**: 구조, 로더, 통계, 정제, 테스트를 완성했다.
- **How**: 작은 함수와 경계값 테스트로 회귀를 막았다.

## Keep
- 구조 먼저, `ddof` 명시, 결측치 이력 보존

## Problem
- 데이터 스키마 검증이 로더 내부에 분산됨
- 이상치 임계값 기준이 문서화되지 않음

## Try
- JSON Schema 기반 입력 검증
- threshold 정책을 설정 파일로 이동
