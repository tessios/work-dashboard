# 업무 대시보드 (Work Dashboard)

개인·업무 현황을 **액션 필요 / 하는 중 / 완료** 세 상태로 한눈에 보는 정적 대시보드입니다.

- 주소: <https://tessios.github.io/work-dashboard/>
- 호스팅: GitHub Pages (`main` 브랜치 root)

## 구조

| 파일 | 역할 |
| --- | --- |
| `index.html` | 화면 전체(HTML·CSS·JS 한 파일). 열릴 때 `tasks.json`을 캐시 없이 다시 읽어 렌더링합니다. |
| `tasks.json` | 표시할 항목 데이터. **이 파일만 수정해 커밋하면** 다음 접속·새로고침에 바로 반영됩니다. |
| `robots.txt`, `.nojekyll` | 검색 노출 차단, GitHub Pages 정적 서빙용 |

`index.html`에는 같은 데이터의 사본이 오프라인/로컬 미리보기용 폴백으로 들어 있습니다. `tasks.json`을 고친 뒤에도 폴백을 맞추려면 빌드 스크립트로 `index.html`을 다시 생성합니다(아래).

## `tasks.json` 형식

```json
{
  "meta": { "version": 1, "updated_at": "2026-11-22T08:30:00+09:00", "updated_label": "2026-11-22 08:30" },
  "items": [
    {
      "id": "blog-inas-2026",
      "status": "action",            // action | progress | done
      "category": "content",         // content | work | review | life
      "area": "블로그",               // 카드 상단 짧은 태그
      "title": "인천아트쇼 2026 발행",
      "summary": "카드에 보이는 한 줄 요약",
      "memo": "상세 시트에 보이는 설명",
      "next": "다음 할 일 (없으면 null)",
      "due": "2026-11-22",           // 마감일 또는 null
      "done_at": "2026-11-21",       // status=done일 때 완료일
      "priority": 1                  // 같은 마감일 안에서 정렬용
    }
  ]
}
```

카테고리: `content` 블로그·콘텐츠, `work` 업무·자격증, `review` 체험단·리뷰, `life` 생활·금융.

## 공개 저장소 주의

이 저장소는 **공개**입니다. `tasks.json`과 코드에 전화번호, 주소, 이메일, 계정 ID·비밀번호, 사내 기밀, 실명, 구체적 계약·금액은 넣지 마세요. 누구나 봐도 안전한 일반화된 업무명과 상태만 담습니다.
