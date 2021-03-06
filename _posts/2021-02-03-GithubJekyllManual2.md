---
title: Jekyll을 이용해서 깃허브로 블로그 만들기_2.포스트, 페이지 작성
date: 2021-02-03
categories: [Manual]
tags: [manual, github, blog, jekyll]
pin: true
math: false
toc: true
toc_sticky: true
description: jekyll에서 포스트와 페이지를 만드는 법에 대해 알아봤다.
---

_※ 본 내용은 2021-02-03 기준으로 작성된 것으로 이 글을 읽는 시점에 따라 적용되지 않을 수 있음._

포스트를 작성하는 것과 페이지를 작성하는 것은 보통 설치한 Jekyll 테마의 Readme.md에 있다. 만약 없다면 사용하지 않는 것을 고려해야 한다.

기본적인 사용법은 다음 사이트에서 찾아볼 수 있다.

[Jekyll Post 작성법](https://jekyllrb-ko.github.io/docs/posts/)

[Jekyll Page 작성법](https://jekyllrb-ko.github.io/docs/pages/)

***

## __포스트 작성__

### __\_posts__

Jekyll이 있는 폴더에 _posts라는 이름으로 새폴더를 만든다. 이미 있다면 새로 만들 필요는 없다.

년도-월-일-제목.md로 파일을 만든다.

2021년 2월 3일에 review라는 제목으로 파일을 만들려면

2021-02-03-review.md 파일을 만들면 된다. 월과 일은 2자리 숫자로 적어야 한다. 제목에는 중간에 띄어쓰기하지 않는다. 띄어쓰기를 해야할 경우 언더바를 사용하면 된다.

포스트 내용에는 마크다운 문법이 적용된다. 그에 관해서 잘 모른다면 해당 내용을 참조한다.

[마크다운 문법 설명서](https://chalgx.github.io/manual/MardkdownSyntax/)

포스트 내부에는 먼저 기본적인 설정을 해야 한다.

\- 표시를 3개 이어 붙인다. 이것을 두 줄을 쓰고 그사이에 필요한 설정을 해야 한다.

사용하는 Jekyll 테마에 따라서, 사용하는 플러그인이나 기타 설정에 따라 적용 가능한 옵션은 다양하다.

예시로는 다음과 같이 쓸 수 있다.

```markdown
---
title: 제목 예시
date: 2021-02-03
categories: [category1]
tags: [tag1, tag2]
description: 
pin: true
math: false
toc: true
toc_sticky: true
---
```

title은 작성하는 포스트의 제목이 된다.

date는 업로드한 날짜로 파일의 이름보다도 우선순위를 가진다.

카테고리와 태그는 여러 개를 작성할 수 있다. 카테고리를 2개 이상 할 경우 그것에 맞게 블로그를 꾸며야 서로 엮이지 않는다. 사용하는 블로그에서 해당 기능이 있는지 확인해봐야 한다. 태그는 소문자로만 이루어지는 게 좋다.

description은 태그에 표시될 설명이다. 해당 포스트가 어떤 글인지 간략하게 적으면 된다.

pin을 true로 두면 포스트가 메인에 보인다.

수식 사용을 지원하는 경우가 있다. 그 경우 math를 true로 둔다면 mathjax 문법을 적용할 수 있다.

toc는 Table of Contents의 약자로 포스트 내용의 목차를 표시해준다. 해당 포스트에 적용된 것이다.

toc_sticky가 true면 toc가 화면이 이동해도 따라간다. 현재 적용되어 있다.

이외에도 다른 요소가 있고 적용 가능한 범위가 다 다르다. 카테고리나 태그에 한글이 안 되는 것도 있다. 잘 따져보고 사용하는 것이 좋다.

### __\_drafts__

_drafts는 초안을 담아두는 폴더다. 없으면 만들면 된다. 사이트를 생성하더라도 해당 폴더 안에 있는 것은 만들어지지 않는다. 글을 담아두고 보관하는 데에 쓸 수 있다.

로컬 서버 실행 시 --drafts를 옵션으로 붙이면 _drafts 폴던 안에 있는 콘텐츠도 페이지가 생성되고 확인할 수 있다. 대신 필요한 양식을 모두 갖춰야 한다.

```ruby
jekyll serve --drafts
```

***

## __페이지 작성__

단순히 포스트를 작성하는 것 외에도 웹페이지 만들 수도 있다.

루트에 바로 페이지를 만들어도 되지만 _pages 폴더를 만들면 편하다. 내부에 .html 파일을 만들거나 .md를 만든다. 마크다운 확장자를 써도 html로 자동으로 변환된다. 처음부터 양식을 꾸미는 것이 힘들면 이미 존재하는 양식을 가져다 쓰고 내용만 바꿔서 사용할 수 있다.

보통 _data에 yml파일이 있고 그곳에는 페이지에 메인페이지와 연동할 수 있는 창 혹은 버튼 같은 것을 생성할 수 있다.

글자에 링크를 연동시키면 해당 단어를 클릭하면 정해진 웹페이지로 자연스럽게 변한다.

머리말에 permalink라 하는 고유주소를 설정하면 등록하는 게 편하다.

_pages 폴더 안에 about.md가 있다면 경로를 /_pages/about.md로 해야 한다. 하지만 about.md 맨 위에 다음과 같은 것을 추가한다고 하자.

```html
---
permalink: /about/
---
```

그러면 /about/만 경로로 설정해도 접속이 가능하다. 이 주소는 다른 것과 겹치면 안 된다.

혹은 _config.yml에 permalink 변수를 추가해서 사용할 수 있다.

***

## __Jekyll을 이용해서 깃허브로 블로그 만들기__

- [1.Jekyll 설치 및 github 연동](https://chalgx.github.io/manual/GithubJekyllManual1/)

- 2.포스트, 페이지 작성

- [3.robots.txt, sitemap, feed 생성 및 설정](https://chalgx.github.io/manual/GithubJekyllManual3/)

- [4.서치 콘솔, 애널리틱스, 웹마스터 연동](https://chalgx.github.io/manual/GithubJekyllManual4/)