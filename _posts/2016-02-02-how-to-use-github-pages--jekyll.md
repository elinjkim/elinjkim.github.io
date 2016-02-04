---
layout: post
title: "How to use Github Pages & Jekyll"
description: "etc"
category: web
tags: [Github Pages, Jekyll, Jekyll Bootstrap]
---
{% include JB/setup %}

<br>

### 깃허브와 지킬로 개인 블로그 만들기 (Github Pages & Jekyll Bootstrap)

<br>

### Before,

기존에 사용하던 블로그 이외에 **"Github Pages"**를 이용한 블로그를 사용해보기로 결심했다.  

<br><br>

### Github Pages

[**Github Pages**](https://pages.github.com)는 Github repository를 기반으로 호스팅되는 웹사이트를 만들 수 있는 개념으로 자세한 사항은 [**Github Pages Help**](https://help.github.com/categories/github-pages-basics/)에서 볼 수 있다.

**Github Pages**의 종류는 아래와 같이 두가지로 구분하며 원하는 방법으로 생성할 수 있다.
 
+ User or Organizaton site  
+ Project site

두 방식은 거의 동일하지만 약간의 중요한 차이가 있다. 
두 방식 모두 HTTPS를 사용하지 않고 HTTP만을 사용하기때문에, repository가 private 하더라도 Pages의 사용에는 주의를 해야한다.

> #### User or Organization site
> <<Username>>.github.io  
> master branch

**User or Organization site**는 Github Pages files로써 Github repository의 특별한(?) 공간에 저장된다.  
이 방식을 사용할 때에는 반드시 자신의 _user name_(account name)을 이용해 repository의 주소를 만들어야하고 이를테면 http(s)://<<Username>>.github.io의 형태이다. 그리고 꼭 master 브랜치를 이용해야 한다. 

<br>

> #### Project site
> <<username or orgname>>.github.io/<<projectname>>  
> gh-pages branch

**Project site**로 Pages를 만들게되면, Project Pages는 해당 프로젝트와 같은 repository에 저장이 된다.   
주소의 형식은 http(s)://<<username or orgname>>.github.io/<<projectname>>과 같으며, 반드시 **gh-pages**라는 브랜치를 만들어 사용해야 한다.    
  
처음에는 **Github Pages** 사이트인 <https://pages.github.com>를 참고했다. 대충 이렇게 하면된다고 이해할 수 있다.  
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

<br><br>

### Jekyll

[**Jekyll**](https://jekyllrb.com/)은 simple, blog-aware, static site를 생성할 수 있게하는 generator라고 설명되어있다.
다 만들고 이 글을 포스팅할 때 알았는데 [[한국어 사이트]](http://jekyllrb-ko.github.io/docs/home/)가 존재했다.

Github Pages는 별도의 DB가 있는 것이 아니기 때문에 페이지를 정적으로 띄운다. 이런 방식을 사용하는 Github Pages에 web의 측면에서 적용하기 아주 적합한 통 프로젝트라고 생각하면 될 것 같다. 
Jekyll은 Ruby 기반으로 되어있기때문에 Ruby가 설치되어 있어야한다. Mac OS X에는 Ruby가 기본으로 설치되어있다. 아래의 명령어로 해당 버전을 확인한다. 

	$ ruby -v

버전이 2.0.0 미만이라면 업그레이드 해주는 것이 좋다고 한다. [**RVM(Ruby Version Manager)**](https://rvm.io/)를 설치한 후 Ruby 버전을 업시키도록 한다. (현재 Jekyll은 Ruby 2.2 버전을 지원하고있다.)

	$ sudo curl -sSL https://get.rvm.io | bash -s stable --ruby
	$ rvm install 2.1.1
	$ rvm --default use 2.1.1
	Using /Users/admin/.rvm/gems/ruby-2.2.1

Jekyll은 Ruby의 gem을 사용해서 설치할 수 있다. gem은 Gemfile이라는 파일을 생성 한 뒤 명령어들을 해당 파일에 작성한 후 실행 명령을 동작시켜주면 된다. [**gems**](https://rubygems.org/search?page=9&query=jekyll&utf8=%E2%9C%93)를 참고하여 파일에 추가한다.

	$ vi Gemfile
	-------------------------------
	source 'https://rubygems.org'
	
	gem 'github-pages'
	gem 'jekyll', '3.1.1'
	...
	-------------------------------
	$ bundle install

Hello World 다음으로 시도했을 때 [**Using Jekyll with Pages**](https://help.github.com/articles/using-jekyll-with-pages/)를 보면서 했는데, Jekyll 사이트의 [**Install with RubyGems**](http://jekyllrb.com/docs/installation/)를 보면 `$ gem install jekyll`의 명령으로 간단히 설치 할 수 있는 것 같다.  


Jekyll 내부에는 웹서버가 동작하고 있어서 해당 웹서버를 동작시켜주면 local에서 확인이 가능하다. 
아래의 명령을 사용하면 레파지토리의 루트로 번들을 이용해 Jekyll 서버를 동작시키는 명령이라고 한다.

	$ bundle exec jekyll serve

나는 아래의 Jekyll 명령으로 동작시켰다. --watch옵션으로 변경사항이 자동으로 업데이트되도록 동작시켰다. `$ jekyll --help` 명령으로 확인할 수 있다.

	$ jekyll serve --watch

Jekyll은 4000번 포트를 사용한다. 즉 localhost:4000으로 확인이 가능하다. 

![image-500](http://cfile9.uf.tistory.com/original/2522E74656AF47B72220A7)

잠시 Jekyll이 설치 된 디렉터리 구조를 살펴보겠다. 아래의 그림은 Jekyll을 설치하 후 `$ tree`명령으로 확인한 로컬에서의 디렉터리 구조이다. 디렉토리 구조에 대해서 자세한 사항은 [**Jekyll Directory structure**](http://jekyllrb.com/docs/structure/)에서 확인하면 된다. 아래의 표는 한국어 사이트에서 번역되어진 내용과 더불어 내 생각을 적은 내용이다(**굵은 글씨**). 웹 개발을 제대로 해본적도 없기 때문에 아주 틀린 정보일 수 있으나, 기억을 위해서 기재한다.

![image-500](http://cfile27.uf.tistory.com/original/2775FC4656AF42BD1B14D3)


| 파일/디렉토리 | 설명 |
| :---: | :---: |
| _config.yml | [[환경설정]](http://jekyllrb-ko.github.io/docs/configuration/) 정보를 보관한다. 명령어를 실행할 때 여러가지 옵션들을 추가할 수도 있지만, 그렇게 따로 외우는 것보다 이 파일에 정의해두는게 더 편리하다. <b>블로그와 사용자 정보를 변경할수 있고 웹 관련 환경설정을 할 수 있다. 또 내가 추가로 플러그인을 사용하고자 할 때, 해당 설정값을 여기서 true로 해야한다. 그리고 기본적으로 commnet기능과 분석기능이 기재되어 있었다. 또 현재 버전부터는 하이라이터로 redcarpet보다 pygments를 사용하는게 가장 좋은 것 같다. YALM 형식으로 작성한다. </b> |
| _drafts | 초안이란 아직 게시하지 않은 포스트를 말한다. 파일명 형식에 날짜가 없다: **title.MARKUP**. 사용 방법은 [[초안 활용하기]](http://jekyllrb-ko.github.io/docs/drafts/)를 참고하라. |
| _includes | 재사용하기 위한 파일을 담는 디렉토리로서, 필요에 따라 포스트나 레이아웃에 손쉽게 삽입할 수 있다.  \{ % include file.ext % \} 와 같이 Liquid 태그를 사용하면 _includes/file.ext 파일에 담긴 코드가 삽입된다. <b>해당 폴더에 들어있는 파일들을 통해서 Liquid가 각 HTML 문서들을 정적으로 모아주는 것 같다. </b> |
| _layouts | 포스트를 포장할 때 사용하는 템플릿이다. 각 포스트 별로 레이아웃을 선택하는 기준은 [[YAML 머리말]](http://jekyllrb-ko.github.io/docs/frontmatter/)이며, 자세한 내용은 다음 섹션에서 설명한다. \{\{ content \}\} 와 같이 Liquid 태그를 사용하면 페이지에 컨텐츠가 주입된다. <b>여기 포함되어있는 html문서들에서 return되어 온 값들이 각각의 html파일들에게 값으로 전달되어 각각의 html 페이지들이 값을 전달받을 수 있는 것 같다. </b> |
| _posts | 한마디로 말하면, 당신의 컨텐츠다. 중요한 것은 파일들의 명명규칙인데, 반드시 다음 형식을 따라야 한다:  **YEAR-MONTH-DAY-title.MARKUP**. [[고유주소]](http://jekyllrb-ko.github.io/docs/permalinks/)는 포스트 별로 각각 정의할 수 있지만, 날짜와 마크업 언어 종류는 오로지 파일명에 의해 결정된다. <b>내가 포스팅하는 파일들이 저장되는 공간이며, Jekyll 템플릿 안에서 Liquid를 통해 자동으로 웹 사이트에서 정적문서로써 포스트섹션으로 처리되는 것 같다. |
| _data | 사이트에 사용할 데이터를 적절한 포맷으로 정리하여 보관하는 디렉토리. Jekyll 엔진은 이 디렉토리에 있는 (확장자와 포맷이 .yml 또는 .yaml, .json, .csv 인) 모든 YAML 파일을 자동으로 읽어들여 **site.data** 로 사용할 수 있도록 만든다. 만약 이 디렉토리에 members.yml 라는 파일이 있다면, site.data.members 라고 입력하여 그 컨텐츠를 사용할 수 있다. <b>이 또한 데이터를 넘겨받는 기능을 제공하는 것 같다. </b> |
| _site | Jekyll 이 변환 작업을 마친 뒤 생성된 사이트가 저장되는 (디폴트) 경로이다. 대부분의 경우, 이 경로를 .gitignore 에 추가하는 것은 괜찮은 생각이다. <b>처음에 해당폴더의 기능이 뭔지 전혀 모르고 추적이 되지않아서 왜그런지 한참 고생했다. 확인은 안해봤지만, 자동으로 .gitignore 설정되어있을지도 모르겠다. </b> |
| .jekyll-metadata | Jekyll 은 이 파일을 참고하여, 마지막으로 빌드한 이후에 한번도 수정되지 않은 파일은 어떤 것인지, 다음 빌드 때 어떤 파일을 다시 생성해야 하는지 판단할 수 있다. 생성된 사이트에 이 파일이 복사되지는 않는다. 대부분의 경우, 이 파일을 .gitignore 에 추가하는 것은 괜찮은 생각이다. |
| index.html 및 다른 HTML, MD, Textfile | ekyll 은 YAML 머리말 섹션을 가진 모든 파일을 찾아 변환 작업을 수행한다. 위에서 언급하지 않은 다른 디렉토리나 사이트의 루트 디렉토리에 있는 모든 .html,  .markdown, .md, .textile 이 여기에 해당한다. <b>말그대로 index 페이지이다. </b> |
| 다른파일/폴더 | css 나 images 폴더, favicon.ico 파일같이 앞서 언급하지 않은 다른 모든 디렉토리와 파일들은 있는 그대로 생성된 사이트에 복사한다. 다른 사람들이 만든 사이트는 어떤식으로 생겼는지 궁금하다면, Jekyll 을 사용하는 사이트들이 이미 많이 있으니 살펴보도록 한다. <b>나는 Jekyll Bootstrap의 테마를 적용 한 후, 검색기능과 테이블 및 이미지 크기변환을 위해서 몇가지 파일을 수정하였다.</b> |

<br>또한 Jekyll은 markdown 형식의 문서에서 [**Front matter**](http://jekyllrb.com/docs/frontmatter/)라는 메타데이터의 세트를 모든 markdown문서의 상단에 기재해야한다. Front matter는 기재할 메타데이터 위아래에 "---"를 사용하여 나타낼 수 있다. "---" 사이에 메타데이터는 생략할 수 있지만 "---"는 꼭 기재해 주어야 한다.
**Front matter**는 당연히 포스팅 문서에도 기재해줘야 하는데, 포스팅 문서의 경우에는 다음과 같을 수 있다.

> \-\-\-  
> title: This is my title  
> layout: post  
> \-\-\-    
> Here is my page.

<br><br>

### Jekyll Bootstrap

처음에는 그냥 Jekyll 기반으로 Pages를 만들었는데 맘에들지 않았다. 그래서 검색해보니 알게된 것이 Jekyll Bootstrap이다.    
[**Jekyll Bootstrap**](http://jekyllbootstrap.com/)은 Jekyll의 기능을 풍부하게 사용할 수 있도록 한다. 내가 Jekyll Bootstrap을 사용하기로 생각한 가장 큰 이유는 테마적용이다. 해당 홈페이지에 들어가면 **"Why JekyllBootstrap?"**이라는 타이틀로 Jekyll Bootstrap을 사용해야하는 이유를 적어놓았다. 해당 내용들이 Jekyll Bootstrap의 주요한 기능이라고 보면 되겠다.
[**Jekyll QuickStart**](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)에서 사용법을 확인할 수 있다.


이제부터는 실제로 내가 Github Pages를 현재의 상태로 적용한 내용을 적어보도록 하겠다. 아예 처음부터 했다는 가정하에 적도록 하겠다. 몇몇 부분은 생략할 수 있다.
순서는 다음과 같다.

1. User Pages를 위한 새로운 Github repository 만들기
2. RVM(Ruby Version Manager) 설치 & Ruby 업그레이드 및 적용 
3. Gemfile을 이용하여 Jekyll 설치 및 버전 업그레이드
4. 내 github에 Jekyll Bootstrap을 clone 하기
5. rake를 이용해서 thema를 설치 후 적용
6. 원격저장소에 push하기  

#### 1. User Pages를 위한 새로운 Github repository 만들기  

첫번째 단계로는 Pages의 repository로 사용될 새로운 repository를 생성해야한다. 
위에도 말했지만 <<Username>>.github.io의 주소로 생성해야한다.

![image-500](http://cfile3.uf.tistory.com/original/2226AF3C56AF2A9C2393B6)

<br>

#### 2. RVM(Ruby Version Manager) 설치 & Ruby 업그레이드 및 적용  

우선 나는 Max OS를 사용하므로 ruby가 미리 설치되어있다. 최소 2.0이상의 버전을 권장하며, 나는 더 높게 버전업 하였다.
버전관리를 위해서 RVM을 설치한다. **위의 내용과 중복된 부분이 있더라 하더라도 다시 적기로 한다.**

	$ rvm -v  
	$ sudo curl -sSL https://get.rvm.io | bash -s stable --ruby  
	$ source /Users/admin/.rvm/scripts/rvm  
	$ rvm --default use 2.1.1
	$ rvm -v  
	
현재 ruby 2.2 버전을 지원하지만 나는 검색하다가 검증되 보이는 2.1.1 버전으로 업그레이드 하였다.

<br>

#### 3. Gemfile을 이용하여 Jekyll 설치 및 버전 업그레이드  

나는 해당 작업들을 위해 **/gitpages**라는 디렉터리를 생성한 후 해당 디렉터리에서 작업하였다.

	$ cd gitpages  

Jekyll은 gem으로 설치할 수 있다. gem에 대해서는 위에서 언급하였다. 
`$ vi`으로 Gemfile이라는 파일을 생성한 후 설치한 패키지를 적는다. 형식은 다음과 같다. 현재 Jekyll은 3.1.1 버전이다.  

	$ vi Gemfile
	-------------------------------
	source 'https://rubygems.org'

	gem 'github-pages'
	gem 'jekyll', '3.1.1'
	...
	-------------------------------
	$ bundle install
	$ bundle upgrade

`$ bundle install`명령으로 설치를 실행할 수 있다. 그리고 github pages에서는 버전 업그레이드(2에서 3으로)를 권장하고 있다. 이를 수행하기 위해서 `$ bundle upgrade`명령도 함께 수행한다.


<br>

#### 4. 내 github에 Jekyll Bootstrap을 clone 하기  

이제 Jekyll Bootstrap repository를 내 repository로 cloning 한다.
이 작업은 내 생각에 github web상에서 fork를 해당 주소를 사용해서 수행해도 될 것 같다. 아무튼 명령어는 다음과 같다.

	$ git clone https://github.com/plusjade/jekyll-bootstrap.git elinjkim.github.io

![image-500](http://cfile30.uf.tistory.com/original/254A333856B2FCDF2D13BA)

#### 5. rake를 이용해서 thema를 설치 후 적용  

[**rake**](http://rake.rubyforge.org/)는 Ruby로 작성된 빌드 툴이다. 자세한건 해당 사이트에서 대충 보도록 한다.  
Jekyll Bootstrap에서 지원하는 기능 중 하나인 thema를 적용시키기 위해서는 rake를 이용한다. 테마적용은 [*여기*](http://jekyllbootstrap.com/usage/jekyll-theming.html)를 보면서 수행했다. 해당 주소로 들어간 후 [**Thema Explore**](http://jekyllbootstrap.com/usage/jekyll-theming.html)를 이용하면 테마들을 미리보기 할 수 있다. Github 페이지는 [*여기*](https://github.com/jekyllbootstrap)를 참고하면 된다.Jekyll Bootstrap을 클로닝 한 후 디렉터리를 살펴보니 Twitter theme는 이미 받아져 있는 것 같다.  
나는 **The-minimum**이라는 테마를 적용하기로 한다. 해당 테마에 맞는 주소를 복붙! 하면된다.

	$ cd elinjkim.github.io  
	$ rake theme:install git="https://github.com/jekyllbootstrap/theme-the-minimum.git"  
	...  
	=> Theme successfully switched!  
	=> Reload your web-page to check it out =)  

	$ rake theme:switch name="the-minimum"  
	...  
	=> Theme successfully switched!  
	=> Reload your web-page to check it out =)  


`$ rake theme:install`명령을 수행하면 자동으로 적용까지 되는 것 같지만 향후 나중을 위해 적용하는 명령어도 함께 수행해 보았다. 이제 서버를 실행 or 재실행 시켜서 확인해보자. 

	$ jekyll serve --watch

**__watch**옵션은 매우 유용하다[^1].

[^1]: 여담이지만 **--watch** 옵션은 정말 유용하게 사용했다. **.md**문서를 작성하는데 오류가 있으면 즉각적으로 debug 메시지가 출력되었기 때문이다. 아래의 이미지에서 정상 동작하던 서버가 어떤 상황에 대해 오류발생에 대한 메시지를 출력하고 있다. ![image-700](http://cfile23.uf.tistory.com/original/274F433856B2FCE0294103)

<br>

Jekyll Bootstrap을 설치하면 이전보다 더 많은 항목들이 생기지만 기본 구조는 같다.

![image-500](http://cfile26.uf.tistory.com/original/24090F3856B313C913DD81)

그리고 테마를 설치하게되면 *../themes/theme_name*의 경로로 항목들이 추가되며 수정도 여기서 하면된다.

![image-500](http://cfile9.uf.tistory.com/original/2403A53856B313CA1863A6)


기존에 있던 샘플 포스트를 지우도록 한다. 그런 후 `$ rake post title=""` 명령을 사용하여 포스트 문서를 생성한다.  
**rake명령어**를 사용하여 포스트를 생성하면 자동으로 **/_posts**에 설정한 title과 현재의 날짜를 기반으로 markdown 문서가 생성된다. 명령어에 `date="2016-02-02"`옵션으로 날짜를 지정할 수 있다. 

	$ rm -rf _posts/core-samples  
	$ rake post title="Welcome to my blog"  
	Creating new post: ./_posts/2016-02-02-welcome-to-my-blog.md  

	$ rake post title="Weloce to my blog" date="2016-02-02"


포스트의 내용을 수정한 후 확인해보자. 아래의 이미지는 해당 포스트파일 생성과 **_config.yml** 환경파일(블로그나 사용자의 정보 등)등 간단한 정보 몇가지를 수정한 후의 모습이다.
 
![image-500](http://cfile21.uf.tistory.com/original/273AFF3856B2FCE339AC0A)

`$ rake`명령을 통해서 문서를 생성하게 되면, 해당 문서의 상위에는 다음과 같이 자동으로 입력되어있다. 명령어로 입력한 데이터가 자동으로 넘어오는 것 같다.  
category나 tag는 자동으로 분류되어 적용된다.

![image-500](http://cfile8.uf.tistory.com/original/263D8A3356B3084716773D)

<br>

#### 6. 원격저장소에 push하기

이제 로컬에서 작업한 이 모든것을 내 원격 저장소인 <elinjkim.github.io>에 적용하도록 한다.

	$ cd elinjkim.github.io  

	$ git init  
	$ git add .  
	$ git commit -m "*commit messge*"  
	$ git remote set-url origin https://github.com/elinjkim/elinjkim.github.io.git  
  	$ git push origin master  
  	To https://github.com/elinjkim/elinjkim.github.io.git
	* [new branch]      master -> master

User pages는 master branch로만 적용해야하므로 간편하다. origin 원격 저장소 설정 후 현재 추적된 것들을 push해주면 끝이다.  
아래의 명령어는 작업 중에 내가 써먹었던 **git명령어**들이다. 아직 git에 완전 익숙치 않아서 적어놓도록 하겠다.

	$ sudo chmod -R g+w wp-content/themes
	$ sudo chmod -R g+w _includes/themes
	$ git remote show origin
	$ git remote -v
	$ git status

<br><br>
모든 기초 작업이 끝났다.  
나는 댓글과 분석 부분은 그냥 사용하도록 두었다. 인터넷에 찾아보니 지원하는 플러그인은 상당히 있는 편인것 같다. 잠깐 다른 것으로 바꿔보기도 했지만, 많은 사람들이 현재 적용되어있는 걸 사용하는 듯 하여, 다시 원래대로 돌려놓았다.

현재 몇가지 적용한 수정사항은 다음과 같으며 이는 나중에 다시 정리해야할 필요가 있는 부분이다.

+ comment부분에서 스폰광고 지움  
+ "search" 탭을 생성 한 후 찾기기능 추가  
+ markdown 문서 작성 시, 테이블이 너무 안예뻐서 css 약간 수정(base.css)

<br><br>

### 참고한 사이트

1. 마크다운 관련  
<http://daringfireball.net/projects/markdown/syntax>
<http://sergeswin.com/1013>  

2. 검색기능 관련  
**Jekyll Search** <http://jekyll.tips/tutorials/search/>  

3. css 관련  
<http://www.w3schools.com/css/css_table.asp>  

4. Github Pages  

5. Jekyll & Jekyll Bootstrap  
<http://jekyllbootstrap.com/>  
<http://jekyllbootstrap.com/usage/jekyll-quick-start.html>  
<http://jekyllrb-ko.github.io/>  

6. Ruby, rake  
<http://rake.rubyforge.org/>  

7. 다음  
**하이라이터 적용하기** <http://hj-lee.github.io/2013/04/05/jekyll-blogging/>  
**시작페이지에 포스팅 수 표시** <http://devblog.croquis.com/ko/2012/05/28/1-jekyll-blog-3.html>  


<br>
<br><br>

- - -
