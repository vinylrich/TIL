# gitflow란?

![image](https://user-images.githubusercontent.com/51067720/133007044-69fd7938-f810-4b59-a6b9-d87b3c1ad4fa.png)


위에 보다싶이 git flow의 브랜치 종류는 세 가지로 나눈다.

1. Main
2. Feature
3. release
4. hotfix

## Main

main 브랜치는 master 브랜치와 develop 브랜치 두 종류를 말한다.

- master

    master 브랜치는 배포 가능한 상태만을 관리하는 브랜치.
- develop

    master 브랜치를 다른 branch로 리모트해서 다음에 배포할 것을 개발하는데, 이 브랜치를 develop 브랜치라고 한다.

## Feature

master 브랜치에서 develop 브랜치를 만들고, 이 develop 브랜치에서 feature 브랜치가 파생된다.

Feature 브랜치는 기능을 개발하는 브랜치이다.

## Release

배포를 위한 최종적인 버그 수정을 개발하는 브랜치이다.

![image](https://user-images.githubusercontent.com/51067720/133007617-9de61451-34f3-4c05-84e8-c43584db5a53.png)
사진을 보면 develop 브랜치에서 버전에 포함된 기능이 모두 구현이 됐으면, QA를 위해 Release 브랜치를 생성한다. 이 프로세스를 모두 끝낸 후 배포 가능한 상태가 되면 release 브랜치를 master 브랜치로 병합시키고, 출시된 master 브랜치에 버전 태그를 추가한다.(ex v0.1,v0.2,v1.0)


## Hotfix

배포한 버전에서(master) 긴급하게 수정할 필요가 있을 때(ex. 게임에서 갑자기 오류가 발생해 점검을 해야할 필요가 있다. 긴급점검과도 비슷한 개념)


## 끝내며
gitflow에 대해서 알아봤는데, 한번 개발할 때도 적용해봐야겠다.


사진 출처: https://overcome-the-limits.tistory.com/entry/%ED%98%91%EC%97%85-%ED%98%91%EC%97%85%EC%9D%84-%EC%9C%84%ED%95%9C-Git-Flow-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0