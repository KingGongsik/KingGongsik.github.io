---
layout: single
title: "[C++ 공부 Day8] "
categories: Study
tag: c++
---

## Day8 - <a href="#first"> 배열과 구조체 </a>, <a href="#second"> 지역변수/전역변수 </a>, <a href="#thrid"> 분할구현 </a>  
  

<p id="first"> # 배열과 구조체 # </p>
  
배열은 보통 int Array[10] = {}; 이런식으로 구현한다.  
배열은 메모리가 연속적인 구조이다. 
   
배열을 쓸때 주의해야할게 예를들어  
int Array[10] = 5;  
이런식으로 배열의 크기를 초과할때 에러가 나지 않는 경우가 있는데 이로 인해 다른 곳에서 에러가 발생할 수 있다.  
  
## 구조체란? ##
사용자 정의 자료형(자료형 : 변수의 데이터 타임)  
typedef : 타입을 재정의 해준다.  
ex) typedef int INT;  
  
c에서는 구조체를  
typedef struct{  
    int a;  
    float b;  
} MYST;  
이런식으로 사용한다.  
C++에서는 typedef를 하지 않아도 되지만 c 코드에서 같이 사용할수있게 typedef 해주는 경우도 있다.  
구조체 초기화는 MYST t = {}; 이런식으로 하면 된다.  

<p id="second"> # 지역변수/전역변수 # </p>  

전역변수 - 사용하는 데이터 영역을 Data 영역이라고 한다.  
  
변수의 종류  

1. 지역변수 - 스택 영역  
2. 전역변수 - 데이터 영역  
3. 정적변수(static) - 데이터 영역  
4. 외부변수(extern) - 데이터 영역  
  
  
메모리 영역  
  
1. 스택 영역  
2. 데이터 영역  
3. 읽기 전용(코드, ROM)  
4. 힙 영역  
  

데이터 영역 : 프로그램이 최초로 실행할때 main()호출 되면서 Data 영역이 만들어짐. 프로그램 종료 시 해제   
  
즉 데이터 영역은 프로그램 시작시 호출되어 종료시 해제가 되는거다. 
  
그러나 전역변수는 데이터 영역에 저장되어 함수의 호출이나 종료에 상관없이 데이터 값을 계속 유지할 수 있다.  


<p id="thrid"> # 분할구현 #</p>  
  
함수를 쓰는 방법 중 1개를 알아보자.  
int Add(int a, int b);  
int main(){  
    Add(4, 3);  
    return 0;  
}  
int Add(int a, int b){  
    return a + b;  
}  
이런식으로 main의 위에서 함수를 선언하고 main 아래에서 기능을 작성해도 된다.  
  
### 그러면 한 스크립트에서 코드를 계속 작성하면 코드가 너무 복잡해지지 않을까? ###  
그래서 헤더와 파일을 만들어 사용한다.  
예를들어 Func.h (헤더파일)을 만들어서 int Add(int a, int b); 이렇게 선언하고  
Func.cpp(일반파일)에 #include"Func.h"로 받아와서  
int Add(int a, int b){  
    return a+b;  
}  
이렇게 한다.  
그 후 main() 함수가 있는 스크립트에서 #include"Func.h"로 받아서 사용하면 된다.  
