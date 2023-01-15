---
title: github blog 제작 일지 #1
author: yuvnn
date: 2023-01-15 17:07:00 +0900
categories: [GitHub Blog]
tags: [GitHub Blog]
---

## 서문 : from scratch!
개발 관련 공부를 기록하는 목적으로 github blog를 제작했습니다! 

웹 전반을 직접 구성해보는 작업은 매우 의미있는 시간이었습니다. 

하지만 git, html, scss 등 웹 개발에 대한 기초 지식없이 맨땅에 헤딩식으로 시작했기 때문에 많은 시행착오를 겪었습니다.

제작하며 엿배운 지식을 조각조각 기록해 놓으려 합니다. 

하지만 부정확한 정보나 미숙한 이해가 있을 수 있는 점 양해 부탁드립니다. ㅠ

( 해당 작업은 window 11 x64 에서 진행하였습니다. )

( 사용한 템플릿은 [jekyll-chrispy-theme](http://jekyllthemes.org/themes/jekyll-theme-chirpy/) 입니다. )
<br>
<br>
## 00. github blog 제작 시작하기
github blog 제작에는 크게 두가지 방법이 있습니다.

1.  [타인의 리포지토리를 fork 하여 사용하기](https://youtu.be/ACzFIAOsfpM)
2. [서버를 구동하고 (jekyll 사용) 자신의 리포지토리에 clone 하기](https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/)

만약 자신의 블로그를 커스텀하지 않아도 되거나, jekyll에 대한 전반적인 이해가 있으신 분들은 1번의 방법을 추천드립니다. 

제작이 보다 간단하기 때문입니다.

하지만 저처럼 초보자이시거나 커스텀이 필요하신 분들은 2번의 방법을 추천드립니다. 

오류해결과 커스텀이 비교적 쉬우며 개념 이해에 많은 도움이 되기 때문입니다.

~~저는 빠르게 해보려고 1번으로 하다가 된통 당하고 두번 갈아엎었습니다~~

혹시나 모르니 제가 참고한 영상과 글을 링크에 다 첨부해 좋겠습니다.
<br>
<br>
**저는 굳이 제작 과정을 전부 서술하지 않겠습니다.**

제가 첨부해 놓은 **링크의 글이나 영상을 따라하는 것 만으로도 충분하기 때문입니다.**

하지만 제작 시 중간중간 오류를 경험할 수 있습니다.

ruby의 버전 변화로 인한 오류나 첨부된 링크의 글 내에 다 서술되지 않은 문제 등이 존재하기 때문입니다.

**이 글은 오류시 참고글 혹은 초보자를 위한 더욱 구체적인 서술 정도로 생각해주시면 감사하겠습니다.**
<br>
<br>
## 01. git push시 오류

모종의 이유로 push 오류가 발생할 때가 있습니다. (캡쳐 없음)

해결방법(2가지) : 


- pull해서 연결하기
  `git pull <repository>`
 - 원격(remote) 폐기 후 다시 연결
 `git remote remove main`
 `git remote add main <repository>`
<br>
<br>
## 02.서버 구동시 오류

###  build site시 오류 

서버를 자신의 리포지토리로 연결하고 배포시 뜨는 오류입니다. 

리포지토리의 상단이나 action 섹션에서 확인할 수 있습니다.

![Desktop View](/assets/img/making-github-blog-img/build-error-img-001.jpg){: width="40%" }

    -----------------------------------------------
      Jekyll 4.2.0   Please append `--trace` to the `serve` command
                     for any additional information or backtrace.
              -----------------------------------------------
            
구글링 결과 $ bundle exec jekyll serve --trace 을 실행해 주면 된다고 하지만 그것은 일시적입니다. 

해결방법 : github\workflows 에서 다음과 같은 코드를 찾아 --trace를 붙여줍니다.

그러면 build마다 workflows에서 bundle exec jekyll serve --trace가 실행됩니다.

![Desktop View](/assets/img/making-github-blog-img/build-error-img-002.jpg){: width="40%" }
<br>
<br>
### .gitmodules 오류

  `fatal: No url found for submodule path 'path/to/submodule'`
  
 이는 리포지토리가 다른 리포지토리에서 복제된 파일을 사용하고 있지만 생성된 소스 리포지토리에 대한 매핑 참조가 없을 때 발생합니다. 
 
 이때 사용 중인 리포지토리의 루트 디렉터리에 있는 .gitmodules 파일에 매핑을 추가하는 방법을 제안합니다. [참고](https://www.deployhq.com/support/common-repository-errors/no-url-found-for-submodule)
 
 
 하지만 저의 경우 계속 제 리포지토리의 경로를 찾을 수 없다는 이해할 수 없는 오류가 떴습니다. 이미 .gitmodules의 path의 원본 링크를 매핑해놓았기 때문에 이는 해결방법이 될 수 없었습니다. 
 

해결방법 : 따라서 그냥 .gitmodules파일을 아예 삭제하고 [이곳](https://github.com/cotes2020/chirpy-static-assets/tree/e372141074f370c6f03b68b5264e7663f2b7477c) (원본 리포지토리) 에서 제안하는 방식대로 .github/workflows/pages-deploy.yml 파일과 _config.yml 파일의 내용을 바꾸었더니 해결되었습니다.

~~해결된 원리는 알 수가 없었습니다. 아시는 분은 알려주십시요..~~
<br>
<br>
### page build 오류


    Process finished with exit code 1
    
page build 과정에서 계속 해당 오류로 빌드가 미실행되었습니다.

해당 오류 내용은 너무 광범위해서 오류 원인을 직관적으로 찾을 수 없었습니다.

하지만 [이곳](https://roadtos7.github.io/android/2021/06/10/Jekyll-FixBuildError.html)의 3번문항에서 오류의 원인을 찾을 수 있었습니다.

저의 경우에서는 _config.yml 에서 tagline의 내용을 !파이팅!으로 적었더니 !을 문자로 인식하지 못해 발생한 오류였습니다. 


해결방법:

    tagline: '!파이팅!'
_config.yml의 내용을 다음과 같이 수정했더니 해결되었습니다. 

문자열을 할당해야 하는 프로퍼티들에는 더블 쿼티션`"` 이나 싱글쿼티션`'`을 사용해야 합니다.

<br>
<br>
---
<br>
<br>
커스텀 시 발생한 오류는 포스팅을 나누도록 하겠습니다.

너무 기록할 생각없이 제작을 했더니 첨부할 자료가 많이 없다는 것이 아쉽네요.

복기하느라 애를 먹어서 실제와 다른 내용이 있을 수 있습니다..

다음부터는 뭘 만들 때 기록하면서 해야겠다는 교훈을 얻고 갑니다.

#2 에서 계속 포스팅하겠습니다!
