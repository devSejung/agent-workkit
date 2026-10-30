# Caveman 원본 설치

세팅할 때 **JuliusBrussee/caveman의 원본 Skill 하나만 설치**한다. 별도 Caveman을 만들거나 내용을 고치지 않는다. 사용자가 지정한 원본과 일치하는 커밋 `4863bc20d9738df2d64870761334b119c3e0c7ce`를 사용한다.

- [원본 SKILL.md](https://raw.githubusercontent.com/JuliusBrussee/caveman/4863bc20d9738df2d64870761334b119c3e0c7ce/skills/caveman/SKILL.md)
- [원본 LICENSE — MIT](https://raw.githubusercontent.com/JuliusBrussee/caveman/4863bc20d9738df2d64870761334b119c3e0c7ce/LICENSE)

제공 Codex가 두 파일을 임시 폴더에 다운로드하고 실제 Skill 본문·라이선스가 모두 도착했는지 확인한 뒤, 제공 버전이 지원하는 Skill 경로에 폴더째 둔다. 과제의 `.agents/skills/caveman/`를 지원하면 그곳을 쓴다. 기존 파일은 덮어쓰지 않는다. 같은 원본 두 파일이 있으면 재사용하고, 충돌하거나 Skill 경로를 쓸 수 없으면 허용된 별도 참고 경로에 둔다. 패키지나 실행 스크립트는 필요 없다.

설치 결과는 **원본 준비 여부와 실제 경로**만 짧게 알린다. 일부만 받았으면 설치 완료라고 하지 않고 Skill 검색 경로에 배치하지 않는다. 다운로드 실패 때문에 본 작업을 멈추거나 Codex·전역 설정을 바꾸지 않는다. [출처와 라이선스](sources.md#caveman-공개-원본을-다운로드해서-사용).

## 사용

아래 문구는 Codex 대화창에 입력한다. 설치만으로 모드를 켜지 않는다.

| 입력 | 동작 |
| --- | --- |
| `$caveman` | CLI가 설치한 원본을 발견했을 때 호출 |
| `짧게` / `caveman 켜` | 설치한 원본 SKILL.md를 실제 경로로 읽어 적용 |
| `짧게 lite` / `짧게 ultra` | 원본이 제공하는 압축 강도 선택 |
| `보통으로` / `normal mode` / `stop caveman` | 해제 |

자동 인식이 안 되거나 동명 Skill의 출처가 불명확하면 `짧게` 또는 “<원본의 실제 경로>/SKILL.md 읽고 적용해”로 바로 쓴다. 새 세션에서는 다시 요청한다. 원본을 받지 못했다면 일반 지시 “핵심만 짧게 답해”로 계속하며, 설치됐다고 주장하지 않는다.

원본의 예외대로 코드·문서는 정상 문체를 유지한다. 실패·미검증·명령·오류 원문·필수 조건을 줄여 없애지 않는다. 시험과 프로젝트 지침이 우선한다.
