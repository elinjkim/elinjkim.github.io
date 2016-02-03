---
layout: post
title: "How to use Github Pages & Jekyll"
description: "etc"
category: web
tags: [Github Pages, Jekyll, Jekyll Bootstrap]
---
{% include JB/setup %}

### How to use Github Pages & Jekyll with Jekyll Bootstrap

### Before,

기존에 사용하던 블로그 이외에 를 이용한 블로그를 사용해보기로 결심했다.  

### Github Pages

Github Pages는 Github repository를 기반으로 호스팅되는 웹사이트를 만들 수 있는 개념으로 자세한 사항은 [Github Pages Help](https://help.github.com/categories/github-pages-basics/)에서 볼 수 있다.

Github Pages의 종류는 아래와 같이 두가지로 구분하며 원하는 방법으로 생성할 수 있다.

+ User or Organizaton site
+ Project site

두 방식은 거의 동일하지만 약간의 중요한 차이가 있다. 
두 방식 모두 HTTPS를 사용하지 않고 HTTP만을 사용하기때문에, repository가 private 하더라도 Pages의 사용에는 주의를 해야한다.

> #### User or Organization site
> <<Username>>.github.io  
> master branch

**User or Organization site**는 Github Pages files로써 Github repository의 특별한(?) 공간에 저장된다.  
이 방식을 사용할 때에는 반드시 자신의 account name을 이용해 repository의 주소를 만들어야하고 이를테면 http(s)://<<Username>>.github.io의 형태이다. 그리고 꼭 master 브랜치를 이용해야 한다. 

> #### Project site
> <<username or orgname>>.github.io/<<projectname>>  
> gh-pages branch


**Project site**로 Pages를 만들게되면, Project Pages는 해당 프로젝트와 같은 repository에 저장이 된다.   
주소의 형식은 http(s)://<<username or orgname>>.github.io/<<projectname>>과 같으며, 반드시 **gh-pages**라는 브랜치를 만들어 사용해야 한다.    
  
처음에는 [Github Pages](https://pages.github.com)를 참고했다. 대충 이렇게 하면된다고 이해할 수 있다.  
User Page를 위해 repository를 username을 사용해 만든 후 똑같이 따라했다.

	$ git clone https://github.com/elinjkim/elinjkim.github.io.git
	$ cd elinjkim.github.io
	$ echo "Hello World" > index.html
	$ git add --all
	$ git commit -m "Initial commit"
	$ git push -u origin master

master 브랜치 그대로 push까지 마치면 내 Page가 만들어진 것을 확인할 수 있게된다.

![image-500](http://cfile3.uf.tistory.com/original/2175773956AF28F620025B)

나는 우선 Git GUI Client(for Windows)를 스터디할 때 아주 살짝 써본게 전부라서 잘 알지 못한다. 그래서 그냥 Mac에서 Xcode를 이용해 Terminal로 작업하였다.  

### Jekyll & Jekyll Bootstrap

[Jekyll](https://jekyllrb.com/)은 simple, blog-aware, static site를 생성할 수 있게하는 generator라고 설명되어있다.
다 만들고 이 글을 포스팅할 때 알았는데 [[한국어 사이트]](http://jekyllrb-ko.github.io/docs/home/)가 존재했다.

Github Pages는 별도의 DB가 있는 것이 아니기때문에 페이지를 정적으로 띄운다. 이런 방식을 사용하는 Github Pages에 web의 측면에서 적용하기 아주 적합한 통 프로젝트라고 생각하면 될 것 같다. 
Jekyll은 Ruby 기반으로 되어있기때문에 Ruby가 설치되어 있어야한다. Mac OS X에는 Ruby가 기본으로 설치되어있다. 아래의 명령어로 해당 버전을 확인한다. 

	$ ruby -v

버전이 2.0.0 미만이라면 업그레이드 해주는 것이 좋다고 한다. [RVM(Ruby Version Manager)](https://rvm.io/)를 설치한 후 Ruby 버전을 업시키도록 한다. (현재 Jekyll은 Ruby 2.2 버전을 지원하고있다.)

	$ sudo curl -sSL https://get.rvm.io | bash -s stable --ruby
	$ rvm install 2.2
	$ rvm --default use 2.2
	Using /Users/admin/.rvm/gems/ruby-2.2.1

Jekyll은 Ruby의 gem을 사용해서 설치할 수 있다. gem은 Gemfile이라는 파일을 생성 한 뒤 명령어들을 해당 파일에 작성한 후 실행 명령을 동작시켜주면 된다. [gems](https://rubygems.org/search?page=9&query=jekyll&utf8=%E2%9C%93)를 참고하여 파일에 추가한다.

	$ vi Gemfile
	-------------------------------
	source 'https://rubygems.org'
	
	gem 'github-pages'
	gem 'jekyll', '3.1.1'
	...
	-------------------------------
	$ bundle install

Hello World 다음으로 시도했을 때 [Using Jekyll with Pages](https://help.github.com/articles/using-jekyll-with-pages/)를 보면서 했는데, Jekyll 사이트의 [Install with RubyGems](http://jekyllrb.com/docs/installation/)를 보면 다음의 명령으로 간단히 설치 할 수 있는 것 같다.

	# gem install jekyll


Jekyll 내부에는 웹서버가 동작하고 있어서 해당 웹서버를 동작시켜주면 local에서 확인이 가능하다. 
아래의 명령을 사용하면 레파지토리의 루트로 번들을 이용해 Jekyll 서버를 동작시키는 명령이라고 한다.

	$ bundle exec jekyll serve

나는 아래의 Jekyll 명령으로 동작시켰다. --watch옵션으로 변경사항이 자동으로 업데이트되도록 동작시켰다. '$ jekyll --help' 명령으로 확인한 것 같은데 다시 해보려니 잘 안나온다.

	$ jekyll serve --watch





- - -


검색기능이 필요했다 
다음을 참고하였다. [Jekyll Search](http://jekyll.tips/tutorials/search/)
	for(var in cycle)
		var += 1;

<code>
1. adfadfadf;  
2. adfadf;
<code>

* * *

***

*****

- - -



*single asterisks*
_single underscores_
**double asterisks**
__double underscores__
++underline++
~~cancelline~~
