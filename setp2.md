# setp2.md — 사용한 gh/git 명령어 목록

## 1. GitHub CLI 인증

```powershell
gh auth login --web --git-protocol https
```

## 2. Git 초기화 및 원격 레포지토리 생성

```powershell
git init
git config user.email "jh19932002-byte@users.noreply.github.com"
git config user.name "jh19932002-byte"
git add -A
git commit --allow-empty -m "Initial commit"
gh repo create ai-issue --public --source . --remote origin --push
```

## 3. 이슈 생성 (배포됨)

```powershell
gh issue create -R jh19932002-byte/ai-issue --title "배포됨" --body " "
```

## 4. 라벨 생성

```powershell
$repo = "jh19932002-byte/ai-issue"

gh label create bug -c E99695 -d "Something is not working" --force -R $repo
gh label create enhancement -c a2eeef -d "New feature or request" --force -R $repo
gh label create documentation -c 0075ca -d "Documentation improvements" --force -R $repo
gh label create question -c d876e3 -d "Further information requested" --force -R $repo
gh label create "help wanted" -c 008672 -d "Extra attention needed" --force -R $repo
gh label create "good first issue" -c 7057ff -d "Good for newcomers" --force -R $repo
gh label create statistics -c 5319e7 -d "Statistical methods and analysis" --force -R $repo
gh label create data -c bfd4f2 -d "Data handling and datasets" --force -R $repo
gh label create testing -c 1d76db -d "Tests and quality assurance" --force -R $repo
gh label create visualization -c c2e0c6 -d "Charts and plots" --force -R $repo
gh label create "priority: high" -c b60205 -d "High priority" --force -R $repo
gh label create "priority: medium" -c fbca04 -d "Medium priority" --force -R $repo
gh label create "priority: low" -c 0e8a16 -d "Low priority" --force -R $repo
```

## 5. 마일스톤 생성 (2주치)

```powershell
gh api repos/jh19932002-byte/ai-issue/milestones -X POST `
  -f title="Week 1: 데이터 탐색 및 기초 통계" `
  -f description="프로젝트 초기 설정, 데이터 로딩, 기초 통계 및 결측치 처리" `
  -f due_on="2026-11-13T23:59:59Z"

gh api repos/jh19932002-byte/ai-issue/milestones -X POST `
  -f title="Week 2: 고급 통계 및 시각화" `
  -f description="가설검정, 회귀분석, 시각화 및 문서화" `
  -f due_on="2026-11-20T23:59:59Z"
```

## 6. 예시 이슈 생성 (Week 1)

```powershell
$repo = "jh19932002-byte/ai-issue"
$m1 = "Week 1: 데이터 탐색 및 기초 통계"

gh issue create -R $repo -t "프로젝트 초기 구조 설정" -b "README, requirements.txt, src/ 및 tests/ 디렉터리 구조를 구성합니다." -l enhancement -l documentation -l "priority: high" -m "$m1"
gh issue create -R $repo -t "CSV/JSON 데이터 로더 구현" -b "pandas 기반 CSV/JSON 로더와 스키마 검증 기능을 구현합니다." -l enhancement -l data -l "priority: medium" -m "$m1"
gh issue create -R $repo -t "기초 통계 함수 구현" -b "평균, 중앙값, 분산, 표준편차 등 기초 통계 함수를 구현합니다." -l enhancement -l statistics -m "$m1"
gh issue create -R $repo -t "결측치 및 이상치 처리 유틸리티" -b "결측치 대치 및 IQR 기반 이상치 필터링 유틸리티를 추가합니다." -l enhancement -l data -l statistics -m "$m1"
gh issue create -R $repo -t "기초 통계 단위 테스트 작성" -b "pytest 기반 단위 테스트와 커버리지 설정을 추가합니다." -l testing -l enhancement -m "$m1"
```

## 7. 예시 이슈 생성 (Week 2)

```powershell
$repo = "jh19932002-byte/ai-issue"
$m2 = "Week 2: 고급 통계 및 시각화"

gh issue create -R $repo -t "가설검정 모듈 추가" -b "t-test, chi-square 등 가설검정 함수를 구현합니다." -l enhancement -l statistics -m "$m2"
gh issue create -R $repo -t "상관분석 및 선형회귀 구현" -b "Pearson/Spearman 상관분석과 OLS 회귀분석 기능을 제공합니다." -l enhancement -l statistics -m "$m2"
gh issue create -R $repo -t "시각화 컴포넌트 구현" -b "matplotlib/seaborn 기반 히스토그램, 박스플롯, 산점도를 제공합니다." -l visualization -l enhancement -m "$m2"
gh issue create -R $repo -t "Jupyter 노트북 예제 추가" -b "통계 워크플로우를 보여주는 예제 노트북을 추가합니다." -l documentation -l enhancement -m "$m2"
gh issue create -R $repo -t "API 문서 및 사용 가이드 작성" -b "함수 문서화와 사용 가이드를 작성합니다." -l documentation -m "$m2"
```

## 8. 확인 명령어

```powershell
git remote -v
gh repo view jh19932002-byte/ai-issue --json name,url,visibility
```
