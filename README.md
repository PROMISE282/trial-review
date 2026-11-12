# trial-review (무료판)

[한국어](README.md) | [English](README.en.md)

> 여러 수정안 중 무엇부터 적용할지, 배심원 5명의 모의 투표로 순위를 내 주는 Claude 스킬의 **무료판**입니다.

소개·동작 방식·판정 기준은 [trial-review-introduction](https://github.com/PROMISE282/trial-review-introduction)에 있습니다. 이 저장소는 무료판 플러그인 파일만 담습니다.

## 무료판에서 되는 것

- 대화에 붙여넣은 수정안·변경안·정책안을 재판 형식으로 평가하고 찬성 비율 순위 표를 냅니다.
- 재판장은 PM이고 배심원은 안건 유형별로 고정된 5명입니다.

| 쟁점 | 배심원 5명 |
| --- | --- |
| 화면·문구 | PM, UX, FE, QA, 일반 사용자 |
| 서버·DB·API·인프라 | PM, BE, 보안, QA, 운영 |
| 정책·기획 | PM, 재무, 운영, CS, 일반 사용자 |

## 무료판의 제약

| 항목 | 무료판 | Pro판 |
| --- | --- | --- |
| 배심원 | 5명 고정 | 안건별 최대 8명, 직무·대상 사용자 선택 |
| 법무 관할 | 법무 직무 없음("법무 검토 필요"만 표시) | 한국 기본, 신호가 있으면 관할 추가 |
| 평가 | 1차(적용 전)만 | 1차 + 적용 후 2차 |
| 입력 | 대화에 붙여넣은 텍스트만 | 코드 저장소·파일 열람 포함 |
| 로컬 변경 | 파일을 읽거나 만들거나 바꾸지 않음 | 작업 사본에서 임시 적용, 승인 뒤 반영 |
| 안건 수 | 한 번에 5건 | 요약 형식, 25건 이상 처리 |

> 이 제약은 스킬 지침(`SKILL.md`)으로 걸려 있습니다. Claude Code의 도구 권한을 기술적으로 막는 것이 아니므로, 도구 사용을 확실히 막으려면 Claude Code의 권한 설정을 함께 쓰세요.

## 설치

### Claude Code (CLI)

```
/plugin marketplace add PROMISE282/trial-review
/plugin install trial-review@promise282-trial-review
```

### Claude Desktop

Claude Code 탭의 플러그인 화면에서 마켓플레이스로 `PROMISE282/trial-review`를 추가한 뒤 `trial-review`를 설치합니다.

> Pro판은 `trial-review-pro`라는 다른 이름이어서 함께 설치해도 호출이 겹치지 않습니다.

### skills CLI (Claude Code, Codex, Cursor 등)

[skills.sh](https://skills.sh)의 CLI로 스킬만 설치할 수도 있습니다.

```
npx skills add PROMISE282/trial-review
```

스킬 폴더(`SKILL.md`, `references/`)만 복사되며 `/trial-review:trial-review` 같은 플러그인 명령은 생기지 않습니다. "재판 형식으로 판단해줘"처럼 말하면 설명문으로 자동 호출됩니다.

## 사용

안건을 대화에 붙여넣고 "재판 형식으로 판단해줘", "배심원 투표로 우선순위 매겨줘", "찬성 비율로 순위"라고 말합니다(영어: "trial review", "jury vote"). 직접 부르려면 `/trial-review:trial-review`를 입력합니다.

파일 경로나 저장소 링크를 주면 열지 않고 안건 내용을 붙여넣어 달라고 안내합니다.

## 한계

- 한 모델이 직무 관점을 흉내 낸 **모의 투표**이며 독립 표본이 아닙니다. 실제 사람의 투표나 통계적 근거가 아닙니다.
- 법무 의견은 제공하지 않으며 법률 자문이 아닙니다.
- 기술 결함 검출은 코드 리뷰와 CI의 몫입니다.
