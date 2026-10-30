# 세팅 시 두 스킬 설치

**Caveman과 explain-work를 Codex의 사용자 스킬 경로에 실제 설치한다.** 참고 폴더에 두거나 경로로 읽기만 하고 세팅을 끝내지 않는다.

1. 제공 Codex의 `skill-installer`가 있으면 그 설치 방식을 사용한다. 기본 목적지는 **`$CODEX_HOME/skills`**, `CODEX_HOME`이 지정되지 않았다면 **`~/.codex/skills`**다. 이미 제공 Codex가 `~/.agents/skills`를 사용자 스킬 경로로 쓰고 있다면 그 경로를 따른다. 환경 변수나 전역 config를 바꿀 필요는 없다.
2. 아래 두 폴더를 설치한다. 설치 도구가 없으면 제공 파일·HTTP 도구로 같은 폴더 구조를 만든다. 과제 README·AGENTS.md·실행 설정은 건드리지 않는다.

| 스킬 폴더 | 설치할 원본 |
| --- | --- |
| `caveman/` | [JuliusBrussee/caveman 원본 SKILL.md와 LICENSE](caveman.md). 원문을 수정하지 않음 |
| `explain-work/` | 가져온 workkit의 `skills/explain-work/` 폴더 전체와 workkit 루트 LICENSE |

최종 형태는 `<사용자 스킬 경로>/caveman/SKILL.md`, `<사용자 스킬 경로>/explain-work/SKILL.md`다. 다운로드는 임시 위치에서 완료한 뒤 설치하고, 원저작자 LICENSE를 각 폴더에 보존한다. 이미 같은 원본이 설치돼 있으면 재사용한다. 다른 기존 스킬은 덮어쓰지 말고 충돌을 알린다.

3. 설치된 파일의 이름·본문을 확인하고 **`/skills` 목록에서 `caveman`과 `explain-work`를 선택할 수 있게 한다.** 현재 세션에서 목록 갱신이 필요한 경우 다음 턴에 다시 확인한다. 그래도 반영되지 않을 때만 작업을 보존하고 Codex 재시작이 필요하다고 안내한다. Codex 업데이트는 하지 않는다.
4. 세팅 결과에 두 스킬의 설치 경로와 목록 확인 상태를 짧게 보여준다. 기본 호출은 **`$caveman`**, **`$explain-work`** 또는 `/skills`에서 선택이다. `짧게`, `서술형 대비해`도 유지한다. 설치만으로 스킬을 실행하지 않는다.

실제 설치 실패·충돌·목록 갱신 문제일 때만 명시 경로 읽기를 임시 대안으로 쓴다. 다운로드 성공을 목록 등록 확인으로 보고하지 않는다. 정상 경로 설치를 생략하는 기본 방식으로 되돌리지 않는다.
