---
layout: single
title: "[C++ 공부 Day11] "
categories: Study
tag: c++
---

## Day11 - <a href="#first"> 포인터 </a>, <a href="#second">  </a>  
  
<p id="first"> # 포인터 # </p>  
  
포인터 : 주소를 가리키는 기능  
포인터 변수 : 포인터 기능을 수행하는 변수  

int* pInt = nullptr;  
이런식으로 포인터 변수를 선언가능 하다.  
nullptr은 0이고 주소에 아무것도 없다는 의미에서 사용한다.  
  
int i = 100;  
int* pInt = &i;  
*은 주소를 저장하겠다는 의미  
&는 주소를 저장하는 변수 의미  
  
(*pInt) = 100;  
저장되어 있는 주소를 참조. 즉 i에 100을 넣겠다는 뜻  
  
주소의 단위는 무엇으로 쓸까? Byte  
100과 102는 2바이트 차이이다.  
  
왜 int형 변수의 주소를 저장하는 변수는 int*로 써야할까?  
int* 변수로 다시 원래값을 불러낼 때 몇 바이트 접근할 지 알아야 하기 때문이다.  
  
그럼 int*로 하고 flaot값을 주면 어떻게 되나?  
float f = 3.f;  
int* pInt = (int*)&f;  
이렇게 할당 가능하다  
이렇게 하면 pInt값이 매우 커지는데 이유는  
int*은 정수형 4바이트 값을 가진다는 뜻이지만 강제로 float형값에서 4바이트를 가지고 와서 엄청 커지게 된다.  


<p id="second"> # # </p>  