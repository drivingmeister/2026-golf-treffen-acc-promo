# Golf Treffen Korea 2026 — Official Merchandise 페이지 (정적 사이트)

서버/DB 없이 동작하는 정적 사이트입니다. 이 폴더를 통째로 웹 호스팅에 올리면 바로 동작합니다.

```
index.html      페이지 전체 (HTML + CSS + JS + 상품 데이터)
img/01~36.webp  상품 이미지 (엑셀 Sheet1 순서와 동일)
img/kv.jpg      KV 배너
img/logo.png    헤더 로고
```

## 배포 방법 (택 1)
- **GitHub Pages** : 저장소에 올린 뒤 Settings → Pages → Branch: main / (root) → `https://<계정>.github.io/<저장소>/`
- **Netlify Drop** : https://app.netlify.com/drop 에 이 폴더를 드래그 → 즉시 URL 발급
- **Vercel / Cloudflare Pages** : 폴더 업로드(Framework: None / Static)
- **자체 서버** : `index.html`과 `img/` 폴더를 같은 경로에 업로드

배포 도메인이 정해지면 `index.html` 상단 `og:image`를 절대 URL(`https://도메인/img/kv.jpg`)로 바꾸고 `og:url`을 추가하면 카카오톡 등 공유 미리보기가 정상 표시됩니다.

## 문구 수정 (index.html)
| 항목 | 위치 |
|---|---|
| 헤더 타이틀 | `<button class="hdr-title" ...>Official Merchandise</button>` |
| KV 안내 문구 | `<p class="kv-lead">` 및 `<ul class="kv-notes">` |
| Disclaimer | `<footer class="disclaimer">` 안의 `<p>` (현재 임시 문구 — 폭스바겐 전달 문구로 교체) |
| 토스트 문구 | `showToast('링크가 복사되었어요🔗')` |

## 상품 데이터 수정
`index.html` 하단 `<script>`의 `var PRODUCTS = [...]` 배열이 상품 목록이며, 배열 순서 = 기본(추천순) 노출 순서입니다.

```
{"n":"상품명","c":"제품코드","d":할인율(%),"p":정가,"s":할인가,"i":"img/파일명","w":이미지가로,"h":이미지세로,"photo":false}
```
- `photo: true` 는 실사 사진(배경이 흰색이 아닌 이미지)일 때만 지정 — 카드 안에 사진 형태로 표시됩니다.
- 상품 이미지는 흰 배경 이미지를 카드 색(#F7F7F7)에 맞춰 넣으면 카드와 자연스럽게 합쳐집니다.

## 동작 메모
- 하트(담기)는 방문자 기기(브라우저 localStorage)에만 저장됩니다. 새로고침해도 유지되며, 서버로 전송되지 않습니다.
- 정렬: 추천순(엑셀 순서) / 가나다순(영문→한글) / 할인순(높은 순) / 가격순(할인가 낮은 순)
- 서체는 Google Fonts(Noto Sans KR)를 불러옵니다. 오프라인 환경에서는 기기 기본 고딕으로 표시됩니다.
