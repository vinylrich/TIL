# Decorator Pattern

---
목차
1. [What is Decorator란?](#Decorator란?)
2. [Code](#구현)
3. [Analysis](#코드-분석)
4. [Field of Application](#활용-분야)

___
## Decorator란?
말 그대로 꾸미기(decorator)가 추가됐다는 뜻. original 기능에서 부가기능을 추가 original기능과는 상관이 없음

기본 글만 쓸 수 있는 볼펜에서 포켓걸이를 넣는다던가, 털실을 붙인다던가 한다는 예시

ex)데이터를 압축을 해서 보내겠다,암호화를 하겠다,log도 보여주겠다,와 같이 원 데이터는 가만히 두고 다른 부가 기능들을 추가하는 디자인패턴 

original 데이터를 바꾸면 soild ocp에 위배됨


![image](https://user-images.githubusercontent.com/51067720/120272488-28582a80-c2e8-11eb-8f68-b01a8ab0e3a3.png)


위 사진에서 기본 기능은 simple window가 있는데 세부 기능인 horizontal,vertical 컴포넌트를 추가한것

vertical을 호출하면 horizontal의 draw가 호출되고-> simplewindow의 draw가 호출됨
얘가 실행이 끝나면 horizontal이 본인의 스크롤바를 호출하고 vertical이 본인의 스크롤바를 호출함


![image](https://user-images.githubusercontent.com/51067720/120273070-fb584780-c2e8-11eb-8440-e48aec4a7943.png)

client는 맨 앞에 있는 operation밖에 모르기 때문에 그냥 호출하는것임

글을 써질거라는건 확신하지만 그 안에서 암호화를 하던 압축을 하던 모르는 일

client가 decortor1의 operator를 호출하면 1이 2를 호출하고, 2가 component의 operator를 호출한다. component까지 간 호출은 2의 함수를 return하고, 2는 1의 함수를 return한다. 결론적으로 client에 보여준다
___
## 구현

data->encrypt->zip(압축)->sends

recevie->upzip->decrypt->data
___
## 코드 분석




___
## 활용 분야

