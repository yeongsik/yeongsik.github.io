# 📝 Jekyll 블로그 포스트 작성 가이드

## 1. 새 포스트 만들기

### 파일 위치 및 명명 규칙
```
_posts/YYYY-MM-DD-제목.md
```

**예시:**
```
_posts/2024-01-15-spring-boot-getting-started.md
_posts/2024-01-16-clean-code-review.md
```

### 기본 포스트 템플릿

```markdown
---
layout: post
title: "포스트 제목"
date: 2024-01-15 10:00:00 +0900
category: backend
tags: [Spring Boot, Java, 백엔드]
excerpt: "이 포스트에 대한 간단한 설명"
---

# 포스트 제목

포스트 내용을 여기에 작성합니다.

## 소제목

내용...

### 더 작은 제목

내용...
```

## 2. Front Matter 설정

### 필수 항목
- `layout: post` - 포스트 레이아웃 사용
- `title` - 포스트 제목
- `date` - 작성 날짜 (YYYY-MM-DD HH:MM:SS +0900)

### 선택 항목
- `category` - 카테고리 (하나만)
- `tags` - 태그 배열 (여러 개 가능)
- `excerpt` - 요약문
- `book_author` - 도서 저자 (독서 포스트용)

### 카테고리 예시
```yaml
category: programming    # 프로그래밍 기초
category: backend       # 백엔드 개발
category: design        # 소프트웨어 설계
category: growth        # 개발자 성장
category: algorithm     # 알고리즘
```

### 태그 예시
```yaml
tags: [Java, Spring Boot, JPA]
tags: [독서, book, Clean Code]
tags: [알고리즘, 코딩테스트, 백준]
```

## 3. 독서 포스트 작성법

### 독서 포스트 템플릿
```markdown
---
layout: post
title: "[독서] Clean Code - 로버트 C. 마틴"
date: 2024-01-15 10:00:00 +0900
category: growth
tags: [독서, book, Clean Code]
book_author: "로버트 C. 마틴"
excerpt: "깨끗한 코드를 작성하는 방법에 대한 실용적인 가이드"
---

## 📖 책 정보
- **제목**: Clean Code
- **저자**: 로버트 C. 마틴
- **출판사**: 인사이트
- **읽은 기간**: 2024.01.01 ~ 2024.01.15

## 🎯 이 책을 선택한 이유
...

## 📝 핵심 내용 정리

### 1장. 깨끗한 코드
...

### 2장. 의미 있는 이름
...

## 💡 인상 깊은 구절
> "깨끗한 코드는 잘 쓴 산문처럼 읽힌다"

## 🚀 실무 적용 계획
...

## ⭐ 평점 및 추천도
- **평점**: 5/5
- **추천 대상**: 모든 개발자
```

## 4. 마크다운 문법 활용

### 코드 블록
```java
public class Example {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### 인라인 코드
`변수명`이나 `메서드명()` 같은 경우

### 인용구
> 중요한 내용이나 책에서 인용한 구절

### 리스트
- 항목 1
- 항목 2
  - 하위 항목
  - 하위 항목

### 번호 목록
1. 첫 번째
2. 두 번째
3. 세 번째

### 링크
[링크 텍스트](https://example.com)

### 이미지
![이미지 설명](이미지-url.png)

### 표
| 컬럼 1 | 컬럼 2 | 컬럼 3 |
|--------|--------|--------|
| 내용 1 | 내용 2 | 내용 3 |
| 내용 4 | 내용 5 | 내용 6 |

## 5. 글 작성 팁

### 제목 작성 가이드
- **일반 포스트**: `Spring Boot 시작하기`
- **독서 포스트**: `[독서] Clean Code - 로버트 C. 마틴`
- **시리즈**: `[Java 기초] 1. 변수와 자료형`
- **문제 해결**: `[트러블슈팅] Spring Boot 빌드 오류 해결`

### 카테고리 분류 기준
- `programming`: Java, Python 등 언어 기초
- `backend`: Spring, Django 등 백엔드 기술
- `design`: 설계 패턴, 아키텍처
- `algorithm`: 알고리즘, 자료구조, 코딩테스트
- `growth`: 개발자 성장, 커리어, 독서

### 태그 사용 가이드
- 구체적인 기술명: `Spring Boot`, `JPA`, `MySQL`
- 일반적인 개념: `OOP`, `TDD`, `리팩토링`
- 독서 관련: `독서`, `book`, `책 제목`
- 시리즈: `Java 기초`, `알고리즘 문제풀이`

## 6. 발행 과정

### 1단계: 파일 생성
```bash
touch _posts/2024-01-15-new-post.md
```

### 2단계: 내용 작성
에디터에서 마크다운으로 작성

### 3단계: 로컬 테스트 (선택사항)
```bash
bundle exec jekyll serve
```

### 4단계: Git 커밋 및 푸시
```bash
git add _posts/2024-01-15-new-post.md
git commit -m "Add new post: 포스트 제목"
git push origin main
```

### 5단계: 자동 배포 확인
GitHub Pages가 자동으로 빌드하고 배포합니다. (몇 분 소요)

## 7. 유용한 VSCode 확장 프로그램

- **Markdown All in One**: 마크다운 편집 도구
- **Markdown Preview Enhanced**: 실시간 미리보기
- **Jekyll Snippets**: Jekyll 문법 자동완성

## 8. 체크리스트

### 발행 전 확인사항
- [ ] 파일명이 올바른 형식인가? (`YYYY-MM-DD-제목.md`)
- [ ] Front Matter가 정확한가?
- [ ] 카테고리와 태그가 적절한가?
- [ ] 마크다운 문법이 올바른가?
- [ ] 코드 블록에 언어가 지정되었나?
- [ ] 이미지가 정상적으로 표시되나?

### 독서 포스트 추가 확인
- [ ] `book_author` 필드가 있나?
- [ ] `독서`, `book` 태그가 있나?
- [ ] 책 정보가 정확한가?

---

💡 **팁**: 정기적으로 글을 작성하는 습관을 만들어보세요. 작은 것이라도 꾸준히 기록하는 것이 중요합니다!