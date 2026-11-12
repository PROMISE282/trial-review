# trial-review

[한국어](README.md) | [English](README.en.md)

> 여러 수정안 중 무엇부터 적용할지, 직무별 배심원의 모의 투표로 순위를 내 주는 Claude 스킬입니다.

소개·동작 방식·판정 기준은 [trial-review-introduction](https://github.com/PROMISE282/trial-review-introduction)에 있습니다. 이 저장소는 플러그인 파일만 담습니다.

피드백은 이 저장소의 [GitHub Issues](https://github.com/PROMISE282/trial-review/issues)나 promise211217@gmail.com으로 보내 주세요.

> **사용자 평가 수집 기간 안내:** 사용자 평가를 원활하게 모으려고 지금은 기능 제한 없이 전체 기능을 풀어 두었습니다. 어느 정도 평가가 모이고 플러그인이 개선되면 예고 없이 성능을 제한하는 업데이트가 있을 수 있습니다.

## 되는 것

- 대화나 코드 저장소·파일에서 수정안·변경안·정책안을 뽑아 재판 형식으로 평가하고 찬성 비율 순위 표를 냅니다.
- 재판장은 PM이고 배심원은 안건별로 최대 8명입니다. 안건의 쟁점에 맞춰 직무와 대상 사용자를 고릅니다.
- 1차(적용 전) 평가와 적용 후 2차 평가를 모두 합니다. 2차용 임시 적용은 작업 사본에서 하고, 반영은 승인 뒤에만 합니다.
- 안건이 많으면 요약 형식으로 처리합니다(25건 이상 포함).

| 쟁점 | 배심원 |
| --- | --- |
| 화면·문구 중심 코드 | PM, UX, FE, BE, QA, A11y, CS, Data |
| 서버·DB·API·인프라 | PM, BE, DBA, 보안, SRE, QA, CS, Data |
| 정책·기획 | PM, 영업, 재무, 법무, 운영, CS, 대상 사용자, Data |

## 설치

### Claude Code (CLI)

```
/plugin marketplace add PROMISE282/trial-review
/plugin install trial-review@promise282-trial-review
```

### Claude Desktop

Claude Code 탭의 플러그인 화면에서 마켓플레이스로 `PROMISE282/trial-review`를 추가한 뒤 `trial-review`를 설치합니다.

### skills CLI (Claude Code, Codex, Cursor 등)

[skills.sh](https://skills.sh)의 CLI로 스킬만 설치할 수도 있습니다.

```
npx skills add PROMISE282/trial-review
```

스킬 폴더(`SKILL.md`, `references/`)만 복사되며 `/trial-review:trial-review` 같은 플러그인 명령은 생기지 않습니다. "재판 형식으로 판단해줘"처럼 말하면 설명문으로 자동 호출됩니다.

## 사용

안건을 대화에 붙여넣거나 파일·저장소를 알려 주고 "재판 형식으로 판단해줘", "배심원 투표로 우선순위 매겨줘", "찬성 비율로 순위"라고 말합니다(영어: "trial review", "jury vote"). 직접 부르려면 `/trial-review:trial-review`를 입력합니다.

## 한계

- 한 모델이 직무 관점을 흉내 낸 **모의 투표**이며 독립 표본이 아닙니다. 실제 사람의 투표나 통계적 근거가 아닙니다.
- 법무 의견은 법률 자문이 아닙니다.
- 기술 결함 검출은 코드 리뷰와 CI의 몫입니다.
