# Postmortem — 대용량 CSV 로딩 중 메모리 초과로 CI 실패

## Summary
- Week 1 데이터 로더 테스트가 500MB CSV 샘플에서 OOM으로 실패했다.

## STAR
- **Situation**: 기초 통계 테스트 CI에서 대용량 입력 처리 중 메모리 초과
- **Task**: 원인 식별과 안전한 로딩 방식 도입
- **Action**: 프로파일링, chunk loading, dtype 최적화, 회귀 테스트 추가
- **Result**: 피크 메모리 70% 절감, CI 안정화

## Why What How
- **Why**: pandas가 전체 CSV를 메모리에 eager 로드했다.
- **What**: 파이프라인 실패와 테스트 중단이 발생했다.
- **How**: chunksize, dtype, 실사용 컬럼 선택, peak memory 테스트를 적용했다.

## Timeline
- 09:00 CI 실패 감지
- 09:20 원인 범위 축소
- 10:10 chunk loading 패치
- 10:40 테스트 재실행 통과

## Root Cause
- 입력 크기와 dtype을 고려하지 않은 전체 로딩
- 메모리 가드레일 부재

## Action Items
- [ ] 로더에 `chunksize` 옵션 추가
- [ ] dtype 추론 대신 명시적 schema 사용
- [ ] peak memory 회귀 테스트 추가
- [ ] 대용량 샘플을 CI fixture에서 제외
