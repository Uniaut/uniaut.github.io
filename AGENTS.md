# geonuchoi.com

최건우의 개인 블로그. 투자 / AI usage / programming 등에 관심.

## Golden rule

### TO DO
* 작업을 마무리 하기 전에 배포가 올바르게 진행될 지 한 번 리뷰를 진행할 것.

### NOT TO DO
* 디자인에는 그닥 관심이 없다.

## Callout (노션 스타일 콜아웃) 사용법

마크다운 아티클 작성을 위해 아래 2가지 방식 중 하나로 노션 스타일 Callout을 바로 사용할 수 있습니다.

### 방법 1: Kramdown 인라인 속성 (권장 - 순수 마크다운)
```markdown
> 💡 **참고 사항**
> 노션 스타일 콜아웃 박스 예시입니다.
{: .callout}
```

타입 지정 (info, warning, danger, success):
```markdown
> ⚠️ **경고**
> 주의가 필요한 내용입니다.
{: .callout .callout-warning}
```

### 방법 2: Liquid 태그 Include
```liquid
{% include callout.html icon="💡" type="info" content="내용을 입력하세요. **마크다운** 문법 지원." %}
```