---
layout: post
title: "Linux Kernel Concept, GNU Linux Distros"
description: "linux kernel concept intro"
category: linux/kernel
tags: [GNU, Linux, Linux Kernel, Linux Distros, Linux Distrobutions]
---
{% include JB/setup %}

<br>

### #1. GNU / Linux Kernel / Linux Distros

<br><br>


### Intro,

작년에 처음으로 리눅스를 접하게 되면서 왜 특히 이 분야에 철학이 중요하다고 하는지 많이 느끼게 되었다.
그런 의미로 리눅스 커널의 개념에 대해서 조금씩 정리를 해볼까 한다.


10개월 동안 **GNU**, **커널**, **배포판** 이라는 단어를 특히 많이 접하게 되었는데 이를 그 첫번째 주제로 해볼까 한다.
[출처-[**Wiki**](https://www.wikipedia.org/)]


<br>

![image-700](http://cfile26.uf.tistory.com/original/24050C3656BF5801058AEA)

<br>

### GNU / GNU Project
[**GNU**](https://ko.wikipedia.org/wiki/GNU)는 **GNU is Not UNIX**의 약자로 GNU는 **GNU Project**를 통해 개발된 UNIX기반의 Software OS이다. 당시 가장 핫하고 안정적이었던 운영체제인 UNIX가 자유 소프트웨어가 아니라는 점에 화(?)가난 [리처드 스톨먼](https://ko.wikipedia.org/wiki/%EB%A6%AC%EC%B2%98%EB%93%9C_%EC%8A%A4%ED%86%A8%EB%A8%BC)이 GNU 개발을 처음 시작하였고 '그누'라고 부르자고 제안하였다.

[**GNU Project**](https://ko.wikipedia.org/wiki/GNU_%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8)는 1983년 9월 GNU선언문을 비롯한 여러 문서와 함께 발표되었으며 사실 리처드 스톨이 설립자이다. 
리처드 스톨은 자유 소프트웨어의 라이센스를 정의하였고 이것이 **GNU GPL(General Public License)**[^1]에 있다.

[^1]: **GNU GPL(General Public License)**는 FSF에서 만든 자유소프트웨어 라이센스이며, 가장 큰 카피레프트이다.  이 라이센스로 되어있는 프로그램을 계승하면 그 역시 GNU GPL을 따라야 한다.  GNU LGPL이라는 것도 있는데 L은 약소되었다는 의미의 Lesser이며 라이브러리 단위를 겨냥한다.  또한 문서 형태에는 GNU FDL(Free Document License)를 사용한다. [*[wiki]*](https://ko.wikipedia.org/wiki/GNU_%EC%9D%BC%EB%B0%98_%EA%B3%B5%EC%A4%91_%EC%82%AC%EC%9A%A9_%ED%97%88%EA%B0%80%EC%84%9C)에서 자세한 정보를 확인할 수 있다.


또 리처드 스톨은 GNU Project를 철학적, 법률적, 자금적으로 조달하기 위해 1985년 [**자유소프트웨어재단(FSF, Free Software Foundation)**](https://ko.wikipedia.org/wiki/%EC%9E%90%EC%9C%A0_%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EC%9E%AC%EB%8B%A8) 또한 설립한다.

GNU Project는 GNU를 완성하기 위해 노력하여 1990년까지 Emacs, gcc, 라이브러리, 유틸리티 등 커널을 제외한 다른 시스템들의 개발을 완료하였다. 하지만 호환에 있어서 커널 개발에는 어려움을 겪고 있었다. 

Trix(MIT), HURD(BSD), Mach

<br>

### Linux / Linux Kernel

마침 1991년 9월, 10월 두차례에 걸쳐 [리누스 토르발즈](https://ko.wikipedia.org/wiki/%EB%A6%AC%EB%88%84%EC%8A%A4_%ED%86%A0%EB%A5%B4%EB%B0%9C%EC%8A%A4)(이하 리누스 토발즈)가 GPL 기반으로 인터넷을 통해 [**Linux Kernel**](https://ko.wikipedia.org/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4)을 공개한다.
(Linux는 본디 커널을 의미한다.) 

리누스가 리눅스를 만들게 된 계기는 자신의 교수인 앤드류 스튜어트 타넨바움이 자신이 개발한 Minix라는 교육용 UNIX를 수업에 활용했지만, 학생들이 개조하지 못하게 제한을 두는것에 대해 불만을 가졌기 때문이라고 한다.
그래서 Linux는 Linu's miniX(리누스의 miniX)를 뜻한다고 하는데 이는 리누스 토발즈가 ftp로 Linux Kernel을 개발하도록 도와준 아리람케라는 사람이 지어주었다고 하며 참고로 처음에 리누스는 리눅스를 freax라고 명명하고 싶었다고 한다.

처음에 Linux는 단순한 에뮬레이터에서 시작으로 파일을 제어하는 기능이 완성되고 [POSIX](https://ko.wikipedia.org/wiki/POSIX) 호환을 목표로 하여 개발이 되었으며, lilo라는 부트로더까지 개발되었다. 
(처음에는 부팅을 위해 Minix같은 다른 프로그램의 도움이 필요했었다.)


1992년 GNU Project와 리누스 토발즈의 Linux Kernel이 결합하여 GNU Project의 유틸리티를 사용하게 됨으로써 [**GNU/Linux**](http://www.gnu.org/gnu/linux-and-gnu.ko.html)라는 OS가 완전공개 되었다.
이것이 우리가 말하는 Linux OS이다.

참고로 Linux 마스코트인 저 펭귄의 이름은 *Tux(턱스)*라고 한다.

<br>

### Linux Distributions(배포판)

이후로 각종 [**배포판(Linux Distributions)**](https://ko.wikipedia.org/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_%EB%B0%B0%ED%8F%AC%ED%8C%90)들이 탄생하게 된다.
Linux Distros는 Linux Kernel, GNU Software 및 각종 free software로 만들어진 UNIX 계열의 OS라고 정의하며 회사차원, 커뮤니티차원 등 다방면으로 만들어지고 사용되어지고 있다. 대표적인 계열로는 <b>Debian, SUSE, Ubuntu, RedHat, Arch, Fedora, SlackWare, Gentoo</b>가 있다.


2016년 가장 핫한 배포판은 다음의 주소로 들어가면 확인할 수 있다.
<https://www.linux.com/news/software/applications/878620-the-best-linux-distros-of-2016>

![image-700](http://cfile27.uf.tistory.com/original/2721553956BF4EC1069AC3)

<br>

리처드 스톨먼이나 리누스 토발즈나 정말 대단한것 같다. 리누스 토발즈는 리눅스 커널관리를 위해 Git까지 개발했고, 소스관리 뿐 아니라 커뮤니티 차원에서도 지금 엄청나게 사용되어지고 있으니..
둘다 구글에 찾아보면 대단한 어록들이 존재하고 또 재미있게 찾아 읽었다. 

그 중 기억에 남는 몇가지는,  
리누스 토발즈가 데이터구조에 대한 중요성을 굉장히 강조한다는 점(참고. [리누스 토발즈가 말하는 좋은 프로그래머](http://yisangwook.tumblr.com/post/82653891224/linus-torvalds-good-programmer))과 리처드 스톨먼이 아직 싱글같다는 점이다(아마도?ㅋㅋㅋㅋ).  


<br><br>

- - -

