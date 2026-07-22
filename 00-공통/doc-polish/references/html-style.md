# HTML 문서 스타일 참고

새 HTML 문서를 만들 때 아래 패턴을 참고한다. 색상·폰트는 문서 성격에 맞게 자유롭게 바꾸되, 구조적 패턴(카드형 컨테이너, 컬러 콜아웃 박스, 헤더 강조)은 유지한다.

## 톤 & 무드
- **다크모드 금지** — 항상 밝은 배경(라이트 모드)으로만 만든다.
- 원색·채도 높은 기본 부트스트랩 톤(진한 파랑 `#007bff`, 진한 빨강 `#dc3545` 등)은 피하고, 더 절제되고 세련된 톤을 쓴다: 무채색에 가까운 배경(`#fafafa`~`#f7f7f8`), 저채도 포인트 컬러, 얇고 정교한 보더/그림자.
- 그림자는 은은하게(`rgba(0,0,0,0.04)~0.08` 수준), 모서리는 너무 둥글지 않게(6~10px 정도).
- 화려한 장식보다 여백과 타이포그래피 위계로 정돈된 느낌을 낸다.

## 기본 구조
- 본문 전체를 감싸는 카드형 `.container` (흰 배경, 둥근 모서리, 은은한 그림자, 옅은 회색 페이지 배경 위에 배치)
- `h1`은 중앙 정렬 + 하단 포인트 컬러 보더
- `h2`는 좌측에 포인트 컬러 굵은 보더 + 왼쪽 여백
- 폰트: 한글 문서는 `'Malgun Gothic', '맑은 고딕', 'Apple SD Gothic Neo', sans-serif` 계열

## 표
- 헤더 행(`th`)은 포인트 컬러 배경 + 흰 글씨
- 짝수 행은 옅은 배경색으로 줄무늬 처리
- hover 시 배경색 살짝 진하게

## 콜아웃 박스 (4종, 왼쪽 굵은 보더 + 옅은 배경)
- **info** (파란 계열): 참고 사항
- **highlight** (노란 계열): 강조할 내용
- **recommendation** (초록 계열): 결론/추천
- **warning** (빨간 계열): 주의사항

## 기타
- 인쇄/PDF 저장 버튼 (`window.print()`), `@media print`로 버튼 숨김·그림자 제거
- 문서 하단에 작성일·작성자 표기

## 예시 (색상은 프로젝트 톤에 맞게 교체 가능, 항상 라이트 톤 기준)
```html
<style>
  body { font-family: 'Malgun Gothic', sans-serif; max-width: 1200px; margin: 0 auto; padding: 20px; background: #f7f7f8; color: #1f2328; }
  .container { background: white; padding: 32px; border-radius: 8px; box-shadow: 0 1px 4px rgba(0,0,0,0.06); }
  h1 { text-align: center; border-bottom: 1px solid var(--accent); padding-bottom: 12px; font-weight: 600; }
  h2 { border-left: 3px solid var(--accent); padding-left: 10px; font-weight: 600; }
  .info { background: #f0f4f8; border-left: 3px solid #5b7ba8; padding: 14px 16px; }
  .highlight { background: #fbf7ee; border-left: 3px solid #c9a04d; padding: 14px 16px; }
  .recommendation { background: #eef4ee; border-left: 3px solid #5a8a5f; padding: 14px 16px; }
  .warning { background: #f8efee; border-left: 3px solid #b0605a; padding: 14px 16px; }
</style>
```
