---
layout: post
title: "Google colab에 module import하기!"
comments: true
description: "Google colab에 module import하기!"
keywords: "dummy content"
---
---

## Google colab에 module import하기!

Local에서 해도 충분하지만.. 갑자기 colab에서 구현해보고 싶은 생각이 들었다.  
( ~~*왜 그랬어 그냥하지..*~~ )  
열심히 **구글링하고 얻은 결과**를 기록하고자 한다.

1. **Colab에서 Google Drive에 있는 파일을 써주려고 하면 mount작업을 먼저 해줘야한다.**

```
from google.colab import drive
drive.mount('/content/drive/')
```
라고 입력하고 google에 로그인해서 코드를 받고 입력하면, drive에 있는 파일들을 `/content/drive/`경로로 확인할 수 있다.

2. **module이 불러져 올 수 있게끔 경로를 설정**

내가 만든 모듈 (*.py)이 `/content/drive/My Drive/Module` 경로에 있다고 하면, 
```
import sys
sys.path.insert(0, '/content/drive/My Drive/Module')
```
 `/content/drive/My Drive/Module`이라는 디렉토리를 경로 0번째 index에 넣어준다.
 
- 경로 확인은 `sys.path`명령어를 통해서 확인할 수 있다.
- *주의점*
   
<img width="923" alt="colab ls" src="https://user-images.githubusercontent.com/35826728/70207853-408ccf00-176f-11ea-9bc1-fdb21cb4aff6.png">  

`!ls, !cd` 등은 띄어쓰기가 있는 경우 "\\"를 띄어쓰기 전에 입력해줘야 되는데, sys.path.insert의 경우 "\\"를 넣으면 "\\"까지 path로 잡히게 되어 module이 불러와지지 않는다.
  
<img width="932" alt="스크린샷 2019-12-05 오후 3 07 24" src="https://user-images.githubusercontent.com/35826728/70208455-f86eac00-1770-11ea-8d12-f11cc0e523bf.png">

3. **Import 하기**

경로설정이 다 되었으므로 `import <module명>`으로 바로 사용하면 된다.