---
layout: post
author: hije
categories: git
tag: everything up-to-date
title: "Git 파헤치기 2 - everything up-to-date 오류"
---
## 오류 - everything up-to-date
* 맨 밑에 상황을 쉽게 정리해뒀다.<br/><br/>
분명 변경사항이 있는데 push 를 했는데도 이 말이 계속 나왔다.<br/><br/>

찾아보니 내가 branch 개념을 제대로 알고 있지 않아서 생긴 상황이었다.<br/><br/>

이유는 엉뚱한 곳에서 작업하고 올바른 곳에 업로드 했기 때문이다.<br/><br/>

나는 사실 지금까지 다른 브랜치에 있는 파일을 작업하고
그곳에 버전을 저장하고 있던 것이다.<br/><br/>

그리고 push만 내가 원하는 branch를 대상으로 한 것이다.<br/><br/>
master이라는 브랜치에서 작업하고 git push origin main이라고
main이라는 브랜치에 push해봤자 이 명령어는 main에 있는 파일들에
대한 commit 상태를 확인하고 github에 push해준다..<br/><br/>

여기서 브랜치를 바꾸면 코드들이 바뀐다 <br/><br/>
내일은 branch 개념을 제대로 정립하자.<br/><br/>

###<정리>
1. apple 이라는 브랜치에 새로운 내용을 올려야한다.
2. 근데 나는 main 브랜치에서 작업했다.
3. apple 브랜치의 내용은 변한게 없다.
4. 그러니까 apple 브랜치를 로컬에서 원격을 푸시했을 때 everything up-to-date 가 뜨는 게 맞다.
5. apple 입장에선 아무것도 한 게 없는데 뭘 업뎃하라는 건가
6. main 에서 apple 로 넘어와서 다시 작업하고 push 하자. <br/><br/>

어 그럼 로컬의 main에서 작업한 걸 원격의 apple로는 못 올리나..? 올릴 수 있겠지.. 내일 알아보자<br/><br/>

[내용 출처](https://velog.io/@max-sum/GitGithub-not-workingeverything-up-to-date-but)
