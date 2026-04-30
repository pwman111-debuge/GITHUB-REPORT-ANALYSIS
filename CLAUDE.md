# Github보고서분석 프로젝트

## 개요
한국 주식 시장 일일 대응 방안 보고서를 자동 생성하고 관리하는 프로젝트.
4개 GitHub 레포(눌림목매매, 눌림목매매2, 교집합매매, 포트폴리오분析)의 데이터를 분석하여 다음 거래일 전략을 수립한다.

## GitHub 연동
- **원격 레포**: https://github.com/pwman111-debuge/GITHUB-REPORT-ANALYSIS
- **브랜치**: `master`
- 이 폴더에서 생성된 보고서 및 수정된 에이전트 코드는 위 레포에 push한다.

## Push 규칙
보고서 생성 또는 에이전트 코드 수정 후 반드시 commit → push를 수행한다.

```bash
git add .
git commit -m "날짜: 변경 내용 요약"
git push origin master
```

## 파일 구조
```
.
├── CLAUDE.md                          # 이 파일 (프로젝트 규칙)
├── .claude/agents/
│   ├── korea-stock-analyzer.md        # 데이터 수집·분석 에이전트
│   ├── korea-stock-reporter.md        # 보고서 생성 에이전트 (자동 저장 포함)
│   └── korea-stock-advisor.md        # 통합 어드바이저 에이전트
└── YYYY-MM-DD_대응방안보고서.md       # 일일 보고서 (대응 날짜 기준 파일명)
```

## 보고서 생성 워크플로우
1. 사용자가 분석 요청 (예: "제네시스 하자")
2. `korea-stock-analyzer` 에이전트 실행 → 4개 레포 데이터 수집
3. `korea-stock-reporter` 에이전트 실행 → 보고서 생성 + 파일 자동 저장
4. 생성 완료 후 commit → push

## 에이전트 수정 시 주의사항
- `.claude/agents/` 내 파일 수정 후 반드시 push하여 버전 관리
- 에이전트 동작 방식 변경은 commit 메시지에 구체적으로 명시
