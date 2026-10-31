# 출처와 채택 범위

확인 기준일: 2026-10-31. 공식 문서는 현재 공개 문서이며 제공 Codex 버전의 동작을 보장하지 않는다. 외부 자료는 이번 시험의 채점표나 기능 허용 근거로 승격하지 않는다.

## 배경과 제품 동작

| 자료 | 반영한 내용 | 한계·저작권 처리 |
| --- | --- | --- |
| [Cofa 인터뷰 정리 — 조쉬의 뉴스레터](https://maily.so/josh/posts/x1zg69d3rqg) | 모호한 요구를 질문으로 구체화, AI 사용 의도, 결과 이해, 익숙한 작업 방식 재사용 | 본문을 읽고 작업 설계의 배경으로 참고. 기사·이미지는 복제하지 않음. 이번 시험의 확정 채점표가 아님 |
| [사용자가 제시한 인터뷰 영상](https://www.youtube.com/watch?v=CLpN3zl8noQ) | 인터뷰 원출처 링크 | 영상 본문은 접근 제한으로 직접 확인하지 못함. 시청·자막 검증을 했다고 주장하지 않음 |
| [OpenAI: AGENTS.md](https://developers.openai.com/codex/guides/agents-md) | 경로·시작 시점에 따른 지침 발견, 별도 clone과 현재 과제 적용의 차이 | 실제 공식 문서 본문 확인. 설정 변경 예제는 복사하지 않음 |
| [OpenAI: Skills](https://developers.openai.com/codex/skills) | 사용자 스킬 설치·자동 발견, `/skills`와 `$skill` 호출 | Caveman·explain-work를 정상 경로에 설치. 외부 Skill 번들·자동 설치기를 복제하지 않음 |
| [OpenAI: Iterating Development Workflows with Codex](https://developers.openai.com/cookbook/examples/codex/iterating-development-workflows-with-codex) | `${CODEX_HOME:-$HOME/.codex}/skills` 사용자 설치 위치 | 제공 skill-installer의 기본 위치를 우선하고 기존 사용자 스킬 경로를 존중 |
| [OpenAI: CLI reference](https://developers.openai.com/codex/cli/reference) | 제공 버전 도움말을 확인한 뒤 이미지 입력을 시험하는 방법 | 현재 `-i`/`--image` 설명을 참고. 제공 환경의 옵션·이미지 동작은 미확인 |
| [OpenAI: CLI 권한 옵션](https://learn.chatgpt.com/docs/cli/reference) | `-a never`와 `-s danger-full-access`의 의미와 구분 | 제공 환경에서 적용 가능한지 미확인. 권한 설정 자동 변경이나 관리자 제한 우회 절차를 넣지 않음 |
| [OpenAI: Developer commands](https://learn.chatgpt.com/docs/developer-commands?surface=cli), [CLI reference](https://learn.chatgpt.com/docs/cli/reference) | `/fork`, `/resume`, `/compact`, `/skills`, 파일 경로 첨부와 셸 명령 구분 | 공식 본문을 읽고 CLI 빠른 사용표를 새로 작성. 제공 버전의 메뉴·도움말이 우선하며 대화 포크를 파일 격리로 취급하지 않음 |

주최 측 안내는 사용자가 전달한 요약을 [환경 문서](environment.md)에 운영 전제로 정리했다. 원문 메일·개인 링크를 수록하거나 독립적으로 확인한 공개 자료처럼 표기하지 않는다. 커뮤니티 체험담은 환경 차이를 점검해야 하는 배경이며 공통 성공법의 증거로 사용하지 않는다.

## Caveman: 공개 원본을 다운로드해서 사용

[JuliusBrussee/caveman의 SKILL.md](https://github.com/JuliusBrussee/caveman/blob/4863bc20d9738df2d64870761334b119c3e0c7ce/skills/caveman/SKILL.md)와 [같은 커밋의 LICENSE](https://github.com/JuliusBrussee/caveman/blob/4863bc20d9738df2d64870761334b119c3e0c7ce/LICENSE)를 실제로 읽었다. 커밋은 `4863bc20d9738df2d64870761334b119c3e0c7ce`, MIT, Copyright (c) 2026 Julius Brussee다. 사용자가 지정한 Skill 본문과 일치하는 버전이다.

별도 재작성본·전체 번들을 이 저장소에 넣지 않는다. 제공 환경의 Codex가 세팅 때 원본 SKILL.md와 해당 LICENSE 두 파일을 내려받게 한다. 원문의 압축 문체·강도·해제 방식을 사용하며 코드·문서의 정상 문체와 명확성이 필요한 예외를 유지한다. 토큰 절감 수치는 이 작업에서 측정하지 않았다. 현재 upstream main의 라이선스와 이 고정 커밋의 MIT를 섞지 않는다. [다운로드·발견·호출 절차](caveman.md).

## 설명 연습 Skill을 만들기 전 비교한 후보

[mattpocock/skills](https://github.com/mattpocock/skills/tree/a496f5513d4a4cf889bc48e189e579f4b0bdf6aa)의 다음 원문과 [LICENSE](https://github.com/mattpocock/skills/blob/a496f5513d4a4cf889bc48e189e579f4b0bdf6aa/LICENSE)를 읽었다. 확인한 커밋은 `a496f5513d4a4cf889bc48e189e579f4b0bdf6aa`, MIT, Copyright (c) 2026 Matt Pocock이다.

| 후보 | 참고한 점 | 그대로 설치하지 않은 이유 |
| --- | --- | --- |
| [grilling](https://github.com/mattpocock/skills/blob/a496f5513d4a4cf889bc48e189e579f4b0bdf6aa/skills/productivity/grilling/SKILL.md) (`grill-me`가 연결) | 질문으로 선택을 구체화하고 사실과 사용자의 결정을 구분 | 설계 면접용으로 여러 질문·권장 답을 제시하고 결정 전체를 순회함 |
| [grill-with-docs](https://github.com/mattpocock/skills/blob/a496f5513d4a4cf889bc48e189e579f4b0bdf6aa/skills/engineering/grill-with-docs/SKILL.md) | 설명을 실제 작업 근거와 연결한다는 방향 | 다른 Skill 호출과 ADR·용어집 작성으로 범위가 커짐 |
| [teach](https://github.com/mattpocock/skills/blob/a496f5513d4a4cf889bc48e189e579f4b0bdf6aa/skills/productivity/teach/SKILL.md) | 스스로 설명하고 피드백받는 연습 | 여러 세션용 학습 공간·HTML 수업·참고 자료를 생성함 |

원문·코드·템플릿을 복제하지 않았다. 질문과 근거 대조 원칙만 참고해 [explain-work](../skills/explain-work/SKILL.md)를 이 사용자의 짧은 작업 이해 점검에 맞춰 자체 작성했다. 선택 이유·실행 결과는 실제 기록과 사용자 답에서만 가져오며, 시험 문제 예측·답안 대필·점수 보장은 하지 않는다. 설치 수나 인지도를 효과 검증으로 취급하지 않는다.

## UI/UX의 보조 근거

다음 공식 문서 본문을 읽고 UI 과제용 점검 원칙을 새로 작성했다. 코드·이미지·디자인 자산은 복사하지 않았다.

| 자료 | 반영한 범위 |
| --- | --- |
| [W3C WAI: Labeling Controls](https://www.w3.org/WAI/tutorials/forms/labels/) | 입력 목적을 설명하는 레이블과 컨트롤 연결 |
| [W3C WAI: User Notifications](https://www.w3.org/WAI/tutorials/forms/notifications/) | 성공·오류 피드백, 이해하고 수정할 수 있는 오류 안내 |
| [web.dev: Responsive web design basics](https://web.dev/articles/responsive-web-design-basics) | 대상 화면에 맞는 콘텐츠 배치와 넘침 점검 |
| [Playwright: Assertions](https://playwright.dev/docs/test-assertions) | 행동 뒤 실제 기대 상태를 검증하는 개념. 도구 도입·시험 사용 허용을 뜻하지 않음 |
| [Vite: Server Options](https://vite.dev/config/server-options) | host 바인딩과 실제 사용 포트가 요청 포트와 다를 수 있다는 점. Vite 설치나 특정 포트를 강제하지 않고 실제 프로젝트 설정을 확인하는 근거로 사용 |

UI/UX 지침은 전체 접근성 표준 준수나 모든 화면 품질을 보장하는 인증 목록이 아니다. 과제의 실제 요구와 확인한 범위에 맞춰 사용한다.

## 의사결정 모델과 제한 시간

아래 공식 문서의 목표·제약·풀이 상태·실행 제한 원칙을 읽고 [의사결정 모델](../playbooks/decision-model.md)을 새로 작성했다. 원문 문구·코드·예제 데이터는 복사하지 않았고 솔버 설치를 기본 구성에 넣지 않았다.

| 자료 | 채택한 범위 / 라이선스 확인 |
| --- | --- |
| [Google OR-Tools: 시작 안내](https://developers.google.com/optimization/introduction/python) | 목표·변수·제약과 문제 유형, 제약 충족과 최적의 구분. 문서 고지: CC BY 4.0, 코드 예제 Apache 2.0 |
| [Google OR-Tools: 탐색 제한](https://developers.google.com/optimization/cp/cp_tasks) | 시간·해 개수 제한 개념. 예제의 수치·언어는 강제하지 않음. 같은 문서·코드 라이선스 고지 확인 |
| [OR-Tools: Troubleshooting](https://github.com/google/or-tools/blob/100f66e6242ab8bf8d32feb8f3bf086db66ae2b5/ortools/sat/docs/troubleshooting.md) | 종료 상태와 모델 오류·불가능 원인 확인. 고정 커밋의 [Apache 2.0 LICENSE](https://github.com/google/or-tools/blob/100f66e6242ab8bf8d32feb8f3bf086db66ae2b5/LICENSE) 본문 확인. 진단 코드·워커 수·외부 전송 예시는 채택하지 않음 |

설명 가능한 기준선을 먼저 실행하고, 질문·실행을 함께 진행하며, 추가 기능에 남은 시간을 배분하는 순서는 이 도구함의 설계 판단이다. 특정 과제의 답·운영 수치·확정 채점표가 아니다. 업무 질문과 시간 관리 지침에는 일반 절차만 남기며 실제 문제·담당자 답변·데이터·작업 기록은 포함하지 않는다.

## 실제 읽은 공개 Skill

전체 Skill·코드·스크립트를 가져오지 않았다. 아래 파일과 LICENSE를 읽고 필요한 원칙만 이 도구함의 범위에 맞춰 한국어로 새로 작성했다. 링크는 확인한 커밋에 고정한다.

| 원본 | 라이선스 | 채택한 부분 | 제외한 부분 |
| --- | --- | --- | --- |
| [obra/superpowers: systematic-debugging](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/skills/systematic-debugging/SKILL.md) | [MIT — Jesse Vincent, 2025](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/LICENSE) | 재현과 원인 근거, 한 가설의 최소 수정, 원래 증상 재검증 → playbooks/debug.md | 모든 버그에 같은 절차·TDD 강제, 특정 횟수 뒤 의무 대화, 도구 예제 |
| [obra/superpowers: verification-before-completion](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/skills/verification-before-completion/SKILL.md) | 위와 같은 MIT | 완료 주장에 맞는 실제 명령·출력·결과 → playbooks/finish.md | 부분 검증을 전부 무효로 취급하는 표현, 매번 전체 검사, 커밋·PR 흐름 |
| [openai/openai-agents-python: code-change-verification](https://github.com/openai/openai-agents-python/blob/cd26bbbc52847845fde73b9952b51e62e2bcbdc0/.agents/skills/code-change-verification/SKILL.md) | [MIT — OpenAI, 2025](https://github.com/openai/openai-agents-python/blob/cd26bbbc52847845fde73b9952b51e62e2bcbdc0/LICENSE) | 수정 중 영향 범위 검사와 완료 시 필요한 검사를 구분 → playbooks/implement.md, finish.md | Python·uv·make 명령, 환경 변수, 실행 정책·샌드박스 예외, 호스트 자원 규칙 |

이 저장소의 오픈소스 탐색 절차는 사용자의 재사용 중심 작업 방식에 맞춰 작성했다. 위 Skill이 모든 후보 탐색이나 라이선스 판단을 해결해 준다고 가정하지 않는다.

유지보수와 실행 근거도 범위를 제한한다. OpenAI Agents Python의 해당 커밋에는 공개 [Tests](https://github.com/openai/openai-agents-python/actions/runs/40571108253) 및 [Code Quality: Scheduled](https://github.com/openai/openai-agents-python/actions/runs/40571725199) 성공 기록을 확인했다. 이는 그 프로젝트의 검사 기록이며 이 도구함의 효과나 시험 호환성을 입증하지 않는다. Superpowers는 원문과 공개 유지보수 기록을 확인했지만 조회한 해당 커밋의 Actions 결과는 없었고, 원본 Skill 자체의 효과는 검증하지 않았다.

추후 외부 코드·문구를 실제 복사하거나 상당 부분 변형해 포함할 때는 해당 버전의 원저작권·LICENSE·필요 고지를 함께 보존한다. 이 저장소의 MIT 표기가 원저작자의 조건을 대체하지 않는다.
