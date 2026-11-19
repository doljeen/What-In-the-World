# GitLab 이력 이관 기록

- 원본: `https://lab.ssafy.com/s15-bigdata-dist-sub1/S15P21D203.git`
- 운영 코드 기준: `a956c1b432c144f73076763da0256294ffe0f107` (`master`)
- 개발 이력 기준: `e7fc9190e91c5529c91d99abe9356a8c1f77679b` (`develop`)
- GitHub의 초기 커밋도 유지했습니다.
- `develop`은 `ours` 전략으로 이력만 연결했습니다. 이 병합은 develop의 코드를 운영 코드에 추가 반영한 것이 아닙니다. 개별 작업 커밋의 출처를 보존하기 위한 이관 작업입니다.
- 원격 GitLab의 네 브랜치는 `archive/gitlab/` 아래에 보존하고, 기존 태그도 함께 옮깁니다. 원격에서 이미 삭제되어 어떤 브랜치·태그에서도 도달할 수 없는 커밋까지 복구한 것은 아닙니다.
- 최초 이관에서는 원본 이력을 유지했습니다. 이후 사용자 요청으로 `redmoon8888@gmail.com`인 author/committer 이메일만 `156649520+doljeen@users.noreply.github.com`으로 바꿨습니다. 이름·시각·트리·메시지·부모 관계와 다른 팀원 정보는 보존했고, 대상 커밋과 후속 커밋의 SHA는 변경되었습니다. 태그도 대응하는 새 커밋을 가리킵니다. 기존 기본 README는 GitLab 원본 커밋에서 확인할 수 있습니다.

## 이관 시 확인 (2026-11-19)

| 항목 | 결과 |
| --- | --- |
| Gitleaks 8.30.1 전체 refs 검사 | 329개 스캔 대상 커밋, 약 17.95MB 검사, 탐지 없음. 도구가 탐지하는 패턴 기준이며 비밀정보 부재를 보증하지는 않음 |
| 프론트 의존성 | 잠금 파일 기준 `npm ci --ignore-scripts` |
| 프론트 빌드 | `npm run build` 성공, 번들 크기 경고 있음 |
| 프론트 테스트 | Node.js 24.20.0에서 107개 중 103개 통과, 4개 실패 |
| 백엔드 통합 테스트 / 실서비스 배포 | 이관 과정에서는 실행하지 않음 |

실패한 기존 테스트:

- `frontend/tests/api.test.js`: 보도 비율 결과 배열의 예상 필드와 실제 필드 차이
- `frontend/tests/mentionLinks.test.js`: 링크 방향 및 튜브 구성 관련 2개 테스트
- `frontend/tests/render.test.js`: 요약 버튼이 추가된 렌더링 결과와 버튼 부재 기대값 차이

이관 과정에서 위 애플리케이션 코드와 테스트는 변경하지 않았습니다. README와 캡처·이관 문서를 추가했습니다.

## GitHub 기여 표시

과거 개인 커밋의 이메일 `redmoon8888@gmail.com`이 다른 본인 계정 `seokjine`에 연결되어 있음을 확인했습니다. 이메일 계정 설정 대신 이 저장소의 개인 커밋 이메일을 `doljeen`의 noreply 주소로 재작성했습니다. 실제 반영 여부는 계정 설정과 GitHub 정책에 따릅니다. 과거 커밋은 원래 날짜에 표시되며 오늘의 기여로 날짜를 바꾸지 않습니다.

[GitHub 공식 기여 누락 안내](https://docs.github.com/en/account-and-profile/how-tos/contribution-settings/troubleshooting-missing-contributions)

## 이메일 재작성 검증

원본 이력은 재작성 전 로컬 bundle로 백업했습니다. 모든 커밋 객체를 비교해 이메일 및 부모 SHA 치환 외의 변경이 없음을 검사했습니다. GitLab 원격은 수정하지 않았습니다. GitHub에서는 기존 원격 SHA를 지정한 force-with-lease와 atomic push로 브랜치·태그를 교체했습니다. README의 커밋 링크도 새 SHA로 수정했습니다.
