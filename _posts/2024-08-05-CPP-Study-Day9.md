---
layout: single
title: "[C++ 공부 Day9] "
categories: Study
tag: c++
---
  
## Day9 - <a href="#first"> 분할 구현의 문제점 </a>, <a href="#second"> 정적변수(Static), 외부변수(extern) </a>  
  

<p id="first"> # 분할 구현의 문제점 # </p>  
  
### 분할 구현을 하는 이유? ###  
- 헤더와 파일 단위로 관련있는 기능들을 묶어서 관리하기 쉽게 하기 위하여.  
  
### 헤더에 참조만 두고 구현은 따로 하는 이유? ###  
- #include 전처리기는 사실상 복사 붙여넣기 이다.  
- 그래서 헤더에 구현을 하면 참조하는 스크립트 모두에 구현되니까 나중에 링크하는 과정에서 똑같은 함수가 여러개 생긴다.  
=> 그래서 헤더에서 선언만 하고 소스코드에 구현을 한다.  
  
### 전역변수는 어떻게 다른 곳에서 사용할 수 있나? ###  
(1) 헤더 파일에 변수를 선언하여 사용하면 될까?  
= 정답은 No이다. 헤더 파일에서 변수를 선언하고 각 스크립트에서 전처리기를 통해서 받아온 뒤 사용을 하면 추후에 링크를 하면서 중복되는 문제가 생긴다.  
이 기능을 위해 
### 정적변수(static)과 외부변수(extern) ###
를 사용해야 한다. 
  


<p id="second"> # 정적변수(Static), 외부변수(extern) # </p>  
  
### 정적변수(static) ###  
각자 자기가 선언된 위치에서 움직이지 않는다. 그래서 각 스크립트에서 같은 이름으로 static을 선언해도 괜찮다.  
=> 나중에 링크를 해도 중복이 되지 않는다.  
  
그러면 static이 함수안에 선언된다면?  
해당 함수에 위치에서 움직이지 않는다.  
  
static은 Data 메모리에 저장된다.  
함수안에서도 똑같다.  
  
함수 정적 변수에서 선언을 하면 함수를 반복 호출 해도 초기화 되지 않고 그냥 초기값으로 사용된다.  
다른 곳에서 함부러 쓰지 못하게 할때 사용한다.  
  
int Test() 
{
	static int i = 0;
	++i;
	return i;
}
int main()
{
	Test();
	Test();
	Test();
	Test();
	int i1 = Test();
	printf("출력값은? %d \n", i1);
	return 0;
} => 이렇게 해도 i1는 5가 제대로 출력된다. 

### 외부변수(extern) ###  
외부변수는 다른 스크립트에서 같은 변수를 사용해야 할때 사용된다.  
이거를 헤더에 비치를 하고 이때 초기값을 주면 안된다.  
이걸 그냥 다른 cpp 파일에서 초기화를 하면 되고 결국 어디에서든 초기값을 주어야한다.  
  
extern int g_iExtern; => 헤더에서 선언
int g_iExtern = 10; => 다른 cpp 파일에서 초기화 
g_iExtern = 599; => 헤더 파일을 전처리기로 가지고 온 스크립트에서 사용 

