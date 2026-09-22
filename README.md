# ZZZ 패턴 연습 배포

[ZZZ 패턴 연습](https://zzz-pattern-practice.github.io/)의 GitHub Pages 배포 저장소입니다. 웹·연구·실험 도구 소스는 [MDYHW/zzz-pattern-practice](https://github.com/MDYHW/zzz-pattern-practice)에 있습니다.

## 최초 설정

이 저장소를 공개(public) 저장소 `zzz-pattern-practice/zzz-pattern-practice.github.io`로 생성하고 workflow를 기본 브랜치에 올린 뒤, Settings → Pages → Build and deployment → Source를 **GitHub Actions**로 설정합니다. 기존 다른 사이트의 설정은 변경하지 않습니다.

## 수동 배포

1. 소스 저장소에서 공개할 커밋의 전체 40자리 SHA를 확인합니다.
2. 이 저장소의 Actions → Deploy practice site → Run workflow를 엽니다.
3. `source_sha`에 소스 SHA를 넣고 실행합니다.
4. 타입·단위 검사·빌드와 배포가 성공하면 표시된 Pages 주소를 확인합니다.

최초 공개 소스 커밋은 `bfdf26560702f1431886fae46a96156686ae7360`입니다. workflow는 입력 형식과 checkout 결과를 확인하고 해당 커밋으로만 빌드합니다. 소스 push만으로 사이트가 배포되지는 않습니다.

공식 GitHub Actions를 커밋 SHA로 고정하며, 배포 저장소의 기본 `GITHUB_TOKEN`으로 동작합니다. 추가 PAT, GitHub App 또는 PEM 파일은 필요하지 않습니다. build에는 소스·Pages 읽기 권한만, deploy에는 Pages와 OIDC 권한을 부여합니다.

## 배포 확인과 되돌리기

사이트 접속, 다섯 패턴 선택, 대표 영상 재생과 환영의 화살 유닛 A/B 전환을 확인합니다. 배포 실패는 Actions의 실패 단계에서 원인을 확인합니다. 배포 후 문제가 있으면 같은 workflow에 이전 정상 소스 SHA를 지정해 다시 배포합니다. 과거 Actions 실행을 다시 실행하는 경우에도 그 실행에서 지정한 소스 SHA를 사용합니다.
