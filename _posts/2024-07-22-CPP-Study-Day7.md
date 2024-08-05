---
layout: single
title: "[C++ 공부 Day7] "
categories: Study
tag: c++
---

## Day7 - <a href="#first"> printf/scanf 입출력 </a>, <a href="#second"> 함수 </a>, <a href="#thrid"> 재귀함수 </a>  

<p id="first">  printf/scanf 입출력 </p>  
  
명령 프롬프트창 : 명령어를 입력 출력한다.  
#include <stdio.h>  
-> 여기서 #include는 전처리기 라고 한다. 헤더 파일을 사용하기 위해 호출하는 데 사용한다.  
  
printf : 콘솔창에 출력  
printf("%d", 4); // 이렇게 %d를 하면 뒤에오는 정수를 출력가능 %f는 실수형 출력  
  
scanf : 콘솔창에 입력  
int iInput;
scanf_s("%d", &iInput); // 입력을 이렇게 받을수있다. scanf는 scanf_s 함수를 사용해야하고 받아오는 값 앞에 &를 해야한다.  

  
<p id="second"> 함수 </p>  
  
main() : 프로그램 실행시 제일 먼저 실행한다.  
  
스택 : 후입선출, 선출후입 구조  
큐 : 선입선출, 후입후출 구조  
  
함수가 사용하는 메모리가 스택 메모리 영역  
코드는 명령어 집합이고 이거를 수행할 떄 수행에 맞춰 동작 하는 곳이 메모리 영역  
코드가 a라는 곳에 집을 지어라 이렇게 온다면 메모리는 집의 크기만큼 지어지고 그후 다시 철거된다.  
함수가 종료되면 메모리가 해제되는 것이다.  
  
함수란?  
- 모듈화 시켜서 코드를 재사용할 수 있다.  
- 기능별로 함수를 잘 만들어두면 나중에 복잡한 기능을 만들때 기존 함수를 합치는 것으로 완성할 수 있다.  
  
  예시로 팩토리얼을 구현해보면 
  int main(){  
    int iValue = 3;  
    int iCount = 1;  
    for(int i = 1; i < iVluase; i++){  
        iCount *= i;  
    }  
  }  
이런식으로 구현할 수 있다. 그런데 이렇게 구현해두면 다른 함수에서 팩토리얼을 사용할 때마다 복사 붙여넣기를 해야한다.  
그래서 이거를 함수로 분리한다.  

int Factorial(int iNumber){  
    int iValue = 1;  
    for(int i = 1; i < iNumber; i++){  
        iValue *= i;  
    }  
}  
int main(){  
    int iValue = Factorial(5);  
}  
이런식으로 사용한다.  

<p id="thrid"> 재귀함수 </p>  
  
함수는 함수 안에서 코드로 자신의 함수를 호출 할 수 있다. 
함수는 스택 메모리여서 함수가 호출될 때 마다 스택에 메모리가 쌓이는데 너무 많이 호출되면 스택 메모리가 가득차 스택 오버플로우가 발생한다.  
  
## 재귀함수란? ##
  
- 자기 자신에서 자신과 같은 함수를 호출하는 함수  
- 위에서 설명한 스택오버플로우를 나타나지 않게 하기 위해 탈출 조건을 만들어야함  
  
재귀함수 장점 
- 프로그램에 익숙해지면 가독성이 좋아지고 구현이 용이하다.  
  
재귀함수 단점  
- 스택오버플로우 발생 위험  
- 성능이 떨어진다. (함수의 반복 호출로 스택에 남아있는 함수 메모리 안의 값들을 변수로 사용해 함수 호출 비용과 해제 비용이 들기 때문)
  
만약 재귀함수로 Fibonacci 구현을 하려면  
int Fibonacci(int iNum){  
    if(iNum == 1 || iNum == 2)  
        return 1;  
    return Fibonacci(iNum -1) + Fibonacci(iNum - 2);  
}  
이렇게 할 수 있다.  
재귀함수가 가독성이 좋은건 맞지만 함수가 계속 호출되어 성능이 느리다.  