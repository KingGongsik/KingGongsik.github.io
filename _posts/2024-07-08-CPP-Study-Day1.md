---
layout: single
title: "[C++ 공부 Day1] "
categories: Study
tag: c++
---


## Day1 - <a href="#first">자료형</a>

<p id="first">  </p>
int i = 0;  
(자료형) (변수명) = (값)  
  
자료형 (크기, 단위)  
정수형 : char(1), shorts(2), int(4), long(4), long long(8)  
실수형 : float(4), double(8)  
  
1바이트는 8비트이다.(비트는 0과 1만 표시 가능)  
1024 byte = 1KB  
1024 KB = 1 MB  
1024 MB = 1 GB  
1024 GB = 1 TB  
  
1 바이트로 표현할 수 있는 비트의 경우의 수는 2^8 = 256가지 이다.   
그러면 1바이트로 표시할 수 있는 정수 범위는?  
양수만 표시한다고 가정하면  
0 ~ 255이다. 
  
자료형에서 양수만 표시하려면 앞에 unsigned를 붙이면 된다. 
unsigned char c = 0;  
  
만약 char c가 256이 된다면?  
1111 1111에서 1이 추가되면 1 0000 0000이 되고 8비트이므로 0000 0000이 되서 0이 된다. 



