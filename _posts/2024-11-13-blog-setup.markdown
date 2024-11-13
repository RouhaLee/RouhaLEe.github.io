---
layout: post
title: "블로그 구축 과정"
date: 2024-11-13
categories: posts
---

## Sum in Blog - 나만의 블로그 구축기

안녕하세요! 이번 글에서는 GitHub Pages와 Jekyll을 활용하여 블로그를 구축한 과정을 공유해볼까 합니다. 이 과정에서 겪었던 문제와 해결 방법도 함께 포함했으니, 블로그를 처음 구축하려는 분들에게 도움이 되기를 바랍니다!

---

### 1. Git과 GitHub 설정

블로그를 구축하기 위해서는 먼저 Git과 GitHub 계정이 필요했어요.

- **Git 설치**: GitHub에서 파일을 푸시하고 관리하려면 Git이 필요하므로, [Git 공식 사이트](https://git-scm.com/)에서 Git을 설치했어요.
- **Git 설정**: 설치 후, 터미널에서 사용자 이름과 이메일을 설정했습니다.

  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "you@example.com"
  ```


### 2. GitHub Pages 리포지토리 생성
다음 단계로 GitHub에 **RouhaLee.github.io**라는 이름으로 새 리포지토리를 만들었어요. GitHub Pages에서 제공하는 무료 호스팅을 활용하기 위해서는 리포지토리 이름이 꼭 username.github.io 형태여야 합니다.

### 3. Jekyll 테마 설치 및 설정

블로그의 디자인을 간편하게 설정하기 위해 **Jekyll**을 사용했어요. Jekyll은 정적 사이트 생성기이며, GitHub Pages에서 기본으로 지원하기 때문에 설치와 관리가 용이합니다.

- **Hyde 테마 선택**: 저는 Hyde라는 테마를 선택했어요. 깔끔한 사이드바와 컬러 옵션이 마음에 들어 선택했습니다.
- **테마 파일 다운로드**: [Hyde 사이트](https://jekyllthemes.io/theme/hyde)에서 Hyde 테마의 파일을 다운로드한 후, 내 리포지토리에 업로드했어요.

### 4. _config.yml 파일 설정

블로그의 기본 정보를 설정하는 `_config.yml` 파일을 수정했어요. 이 파일에서 사이트 제목, 설명, 작성자 정보, 기본 경로 등을 설정할 수 있습니다.

- **baseurl**: 로컬 환경에서는 빈 값으로 설정해야 경로가 제대로 작동해요.
- **테마 설정**: Hyde 테마는 여러 색상 옵션을 제공하기 때문에, `theme-base-0c`와 같이 설정해서 하늘색 테마로 바꿨어요.

  ```yaml
  title: "Sum in Blog"
  description: "무언가를 깨트리는 것은 경계를 부풀리는 새로움을 전해줄 것이다"
  baseurl: ""
  theme: theme-base-0c
  ```


### 5. 사이드바 커스터마이징

기본적으로 제공되는 사이드바 메뉴를 저만의 스타일에 맞게 바꿨어요. `sidebar.html` 파일을 수정하여 **Home**, **about**, **posts**라는 메뉴 항목을 추가했습니다.

```html
<nav class="sidebar-nav">
  <a class="sidebar-nav-item{% if page.url == '/' %} active{% endif %}" href="/">Home</a>
  <a class="sidebar-nav-item{% if page.url == '/about/' %} active{% endif %}" href="/about">about</a>
  <a class="sidebar-nav-item{% if page.url == '/note/' %} active{% endif %}" href="/note">posts</a>
</nav> 
```

### 6. About 및 Posts 페이지 생성

`about.md`와 `note.md` 파일을 루트 디렉토리에 생성하여, 소개와 글 작성 페이지를 따로 만들었어요.

- **about.md**: 소개 페이지로 설정하여, 제 소개와 관심사를 작성했습니다.
- **note.md**: posts 페이지로 설정해, 작성한 글 목록이 표시되도록 했어요.

  ```markdown
  ---
  layout: page
  title: posts
  permalink: /note/
  ---

  <h2>Posts</h2>
  <ul>
    {% raw %}{% for post in site.posts %}{% endraw %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <span>{{ post.date | date: "%Y-%m-%d" }}</span>
      </li>
    {% raw %}{% endfor %}{% endraw %}
  </ul>
  ```

### 7. CSS 경로 문제 해결

메인 페이지에서는 CSS가 잘 적용되었지만, 다른 페이지에서는 CSS가 로드되지 않는 문제가 발생했어요. 이를 해결하기 위해 `site.baseurl` 뒤에 `/`를 추가해 경로를 수정했습니다.

```html
<link rel="stylesheet" href="{{ site.baseurl }}/public/css/poole.css">
<link rel="stylesheet" href="{{ site.baseurl }}/public/css/syntax.css">
<link rel="stylesheet" href="{{ site.baseurl }}/public/css/hyde.css">
```

### 8. 첫 게시글 작성

블로그 구축이 완료된 후 `_posts` 폴더에 첫 게시글을 작성했어요. Jekyll에서는 **YYYY-MM-DD-title.md** 형식으로 파일 이름을 설정하고, Markdown 문법을 이용해 글을 작성할 수 있어요.

```markdown
---
layout: post
title: "나의 첫 게시글"
date: 2024-11-12
categories: posts
---

블로그 내용 

```

---
이렇게 해서 Sum in Blog라는 저만의 블로그를 완성했어요! 블로그를 구축하면서 겪었던 문제를 해결하고, 원하는 대로 디자인을 커스터마이징하는 과정이 재미있었습니다. 이번 포스팅이 여러분에게도 도움이 되길 바랍니다. 좋은 하루 되시기를! 😊