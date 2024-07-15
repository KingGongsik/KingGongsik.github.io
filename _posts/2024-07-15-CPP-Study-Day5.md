---
layout: single
title: "[C++ 공부 Day5] "
categories: Study
tag: c++
---



## Day5 - <a href="#first"> Switch/case와 삼항 연산자 </a>, <a href="#second"> Define </a>, <a href="#thrid">비트 연산자</a>  
  


<p id="first">  switch / case  </p>  
  
if / else와 비슷한 기능으로 switch case가 있다.  
비슷한 기능인데 왜 switch / case를 만들었을까?  
사실 문법적으로 차이는 없다.  
하지만 switch / case로 표현하기 어려운 경우가 if / else로 표현하기 쉬울때가 있고  
if / else로 가독성이 좋게 만들기 어려울때 switch / case로 가독성 좋게 만들수 있어서 상황에 따라 적절히 쓸 수 있어야 한다.  
  
삼항 연산자  
if / else문이나 switch / case문을 한줄로 쉽게 표현할 수 있다.  
if(iTest == 10){  
    iTest = 100;  
}else{  
iTest = 200;  
}  
을 iTest == 10? iTest = 100 : iTest = 200;  
이런 식으로 줄일 수 있다.  
하지만 조건이 더 길어지면 가독성이 좋지 않아서 자주 사용하지는 않는다.  
  
  

<p id="second">  Define  </p>  
define 전처리기는 특정 문자를 값으로 치환하는 것이다.  
예를 들어 #define HUNGRY 1 은 HUNGRY를 1로 치환하는 것이다.  
왜 전처리기를 사용할까?  
(1) 게임에서 화상 상태, 공복 상태 등 상태 이상을 가독성 좋게 알려줄 수 있다.  
(2) 해당 상태의 값이 변경되더라도 다른곳 수정을 안해도 된다. (유지보수에 좋다.)  
  
  
  
<p id="thrid">  비트 연산자  </p>  
비트 연산자는 비트 단위로 연산이 진행될 때 사용되는 연산자이다.  
쉬프트 (<<, >>)
unsigned char a = 1;  
a << = 1;  이면 한칸씩 왼쪽으로 비트가 밀려서 1칸당 2씩 커진다.  
즉 a <<= b;이면 a가 2^b만큼 커진다.  
반대로 a >>= b;이면 a가 1/2^b만큼 작아진다는 것이다.  
  
비트 곱(&), 합(|), xor(^), 반전(~)  
전부 비트 단위로 연산을 진행한다.  
& 둘다 1이면 1, 아니면 0  
| 둘 중 하나라도 1이면 1 아니면 0  
^ 같으면 0 다르면 1  
~ 0이면 1, 1이면 0  
  
  
# 비트 연산자를 언제 사용하는 건가? #
  
비트 연산자를 사용하는 경우?는 예를 들어 플레이어 상태 이상을 제어할때 값을 unsigned int pState;로 두면은  
int형인 pState는 4바이트이므로 각 상태 이상을 1자리씩 두면 총 32개의 상태이상을 나타낼 수 있다. 
즉   
#define HUNGRY 1  
#define TIRED 2  
#define THIRSTY 4  
이렇게 되어 있을때 pState |= HUNGRY; 이런식으로 상태를 추가할 수 있다.  
그리고 상태를 확인하고 싶을때는 if(pState & HUNGRY) 이런 식으로 확인하면 되며  
상태 이상을 해제하고 싶을때는 pState &= ~HUNGRY; 이런식으로 해제하면 된다.  
  
추가로 define에 값을 줄때 2의 배수로 줘야하는데 계산하기 복잡해서 보통  
#define HUNGRY 0x001    
#define TIRED 0x002  
#define THIRSTY 0x004  
#define HUNGRY 0x008  
#define TIRED 0x010  
#define THIRSTY 0x020  
#define HUNGRY 0x040  
#define TIRED 0x080  
#define THIRSTY 0x100  
#define TIRED 0x200  
#define THIRSTY 0x400  
#define THIRSTY 0x800  
이런식으로 값을 쓰고 이름을 바꿔주면 된다. 



