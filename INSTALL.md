# 설치 방법

## 1. 레포 클론 (컴퓨터당 1번만)

```bash
git clone https://github.com/elfinnani-byte/my-skills.git ~/my-skills
```

## 2. 스킬을 Claude Code가 인식하는 위치로 심볼릭 링크 (컴퓨터당 1번만)

Claude Code는 `~/.claude/skills/<스킬명>/SKILL.md` 형태의 평평한 구조를 인식한다. 이 레포는 단계별 폴더로 관리하므로, 심볼릭 링크로 연결한다.

```bash
mkdir -p ~/.claude/skills
for dir in ~/my-skills/*/*/; do
  name=$(basename "$dir")
  ln -sf "$dir" ~/.claude/skills/"$name"
done
```

이렇게 하면 레포는 단계별 폴더 그대로 유지되고, `~/.claude/skills/`에는 모든 스킬이 평평하게 연결되어 어떤 프로젝트에서든 자동으로 인식된다.

## 3. 레포에 새 스킬을 추가했을 때

```bash
cd ~/my-skills && git pull
# 위 2번의 for 루프를 다시 실행 (새로 추가된 폴더만 새로 링크됨)
```

## 4. 프로젝트별 CLAUDE.md에 추가하기 (프로젝트마다)

전역 설치는 한 번이면 끝이지만, 각 프로젝트의 `CLAUDE.md`에는 아래처럼 "이 단계엔 이 스킬" 안내를 추가해두면 Claude가 상황에 맞는 스킬을 더 잘 찾아 쓴다.

```markdown
## 사용 가능한 개인 스킬 (my-skills)

`~/.claude/skills/`에 설치된 바이브 코딩 스킬을 프로젝트 단계에 맞춰 사용한다. (레포: elfinnani-byte/my-skills)

| 단계 | 상황 | 스킬 |
|---|---|---|
| 기획 | 새 프로젝트/모듈 시작 | `project-kickoff-scaffolder` |
| 기획 | DB 테이블·RLS 설계 | `db-schema-rls-reviewer` |
| 기획 | 여러 기획 문서 정합성 확인 | `doc-consistency` |
| 개발 | 커밋 메시지 정리 | `commit-summary` |
| 개발 | 에러/버그 해결 | `debug-session` |
| 개발 | 코드 리뷰 및 최적화 | `code-review-optimize` |
| 개발 | 브랜치 전략 수립 | `git-branch-strategy` |
| 디자인 | 스타일 가이드 확인/갱신 | `style-guide` |
| 디자인 | 새 화면 설계 | `screen-design-new` |
| 디자인 | 기존 화면 검토 | `screen-design-review` |
| QA | 테스트 전략 수립 | `test-strategy` |
| 배포 | 배포 전 점검 | `deploy-checklist` |
| 공통 | 세션 마무리 | `session-handoff` |
| 공통 | 문서 서식/변환 | `doc-polish` |

작업 단계가 바뀌거나 위 상황에 해당하면, 명시적 요청이 없어도 관련 스킬을 먼저 사용할지 확인한다.
```
