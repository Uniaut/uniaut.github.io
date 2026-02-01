# uniaut.github.io

Jekyll 기반 개인 블로그

🌐 **사이트**: [https://uniaut.github.io](https://uniaut.github.io)

## 🎨 특징

- **미니멀리즘**: Black & White 컬러 스킴
- **타이포그래피**: Pretendard 폰트
- **반응형 디자인**: 모바일부터 데스크탑까지
- **자동 배포**: GitHub Actions

## 📝 글 작성 방법

### 1. 로컬에서 작성

```bash
cd _posts
```

새 파일 생성 (형식: `YYYY-MM-DD-title.md`):

```markdown
---
layout: post
title: "글 제목"
date: 2026-02-01
categories: [카테고리]
---

글 내용을 작성합니다...
```

### 2. Git으로 푸시

```bash
git add .
git commit -m "Add new post: 글 제목"
git push origin main
```

### 3. 자동 배포

GitHub Actions가 자동으로 빌드하고 배포합니다 (약 1-2분 소요).

## 💻 로컬 개발

Ruby 3.2 이상 필요:

```bash
bundle install
bundle exec jekyll serve
```

`http://localhost:4000`에서 확인 가능합니다.

## 📁 프로젝트 구조

```
.
├── _posts/              # 블로그 글 (YYYY-MM-DD-title.md)
├── _layouts/            # 페이지 레이아웃
├── _includes/           # 재사용 가능한 부분 (header, footer 등)
├── assets/
│   └── css/            # 스타일시트
├── _config.yml         # Jekyll 설정
├── index.md            # About Me (홈페이지)
└── articles.md         # 글 목록 페이지
```

## 🚀 다른 기기에서 글 작성하기

### 방법 1: Git 사용
```bash
git clone https://github.com/Uniaut/uniaut.github.io.git
cd uniaut.github.io
# 글 작성
git add . && git commit -m "메시지" && git push
```

### 방법 2: GitHub 웹 인터페이스
1. [_posts 디렉토리](https://github.com/Uniaut/uniaut.github.io/tree/main/_posts) 이동
2. "Add file" > "Create new file" 클릭
3. 파일명: `YYYY-MM-DD-title.md`
4. 내용 작성 후 "Commit changes" 클릭

## 📧 연락처

- Email: kunwoo0927@gmail.com
- GitHub: [@uniaut](https://github.com/uniaut)
- LinkedIn: [최건우](https://www.linkedin.com/in/건우-최-7362ba2b2)
