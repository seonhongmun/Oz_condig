## 입력과 출력

* 입력 : input()
* 출력 : print()

## 함수와 메서드
    > 함수 : 어디에 속해있지 않고 단독 모듈이라 함수를 그냥 호출하여 사용이 가능하다.
        예> print(), input()  

    > 메소드 : 함수의 클래스 안에 속해 있고 클래스의 멤버 변수들을 이용해서 구현된 것  
        예> "까먹으신건가요?   
    ** .count("까") : "까"가 몇개나 있는지 확인하는 명령어   
    ** .index("까") : "까"의 위치를 알수 있는 명령어    
## 시퀀스 자료형
# * 문자열 :
        * 시퀀스형에서 사용할수 있는 메소드(count(), index(), split() 등..)
        * 슬라이싱 ([:][::])
        * 요소들로 이루어져 가능했던 기능들 (요소 합치기, 요소 찾기 등등)
# * list :
        * 시퀀스형에서 사용할수 있는 메소드(count(), index(), split() 등..)
        * 슬라이싱 ([:][::])
        * 요소들로 이루어져 가능했던 기능들 (요소 합치기, 요소 찾기 등등)
        * list 지원하는 다양한 메소드 (adppend(), insert(), del, sort(), reverse_)
# * tuple :
        * 리스트처럼 요소를 일렬로 저장하지만 안에 저장된 요소를 변경, 추가, 삭제할 수 없다.
        * 값을 추가, 삭제, 변경할 수 없기 때문에, 사용하지 못하는 메소드가 많다.
        * tuple의 생성 방법은 tuple = 값, 값 또는 tuple = (값, 값)
        * tuple은 소괄호이다.
# * dict(딕셔너리)
        * list, tuple, str, range(범위안에 연속된 데이터를 만드는 시퀀스)
            > 공통적인 특징이 있지만 데이터의 연관성은 없다.
        * dict은 여러개의 값이 일렬로 정렬되면서도 값끼리의 연관성이 존재
        (예시 : 게임 캐릭터 힘 :30. 지능 : 20 , 체력 :40 , 민첩 : 90)
        * dict 생성방법은 중괄호
# * set
        * set은 수학의 집합을 의미한다.
        * 딕셔너리와 같이 순서가 없다.
        * 값의 중복을 허락하지 않는다. 아주 중요!!
        * set 생성 방법도 중요
### 정리본 코랩 
   > url : https://colab.research.google.com/drive/1gveVX35nUzwb_btWjPTScjM4wy-f9Ld1 
   > url : https://colab.research.google.com/drive/1_3B-0ffgYwyVZPl4DJaUjG0kjvOl5-H5
   > url : https://colab.research.google.com/drive/11yZSkZC2S_6S8EQwHruPLKSki04sp0__
   > url : https://colab.research.google.com/drive/1iSyjgJS-skp-9gVtepmcnLFND1HTj66n
   > url : https://colab.research.google.com/drive/18JHv7V6VaqObydJPJ8F2ya-NjrFBXfhs#scrollTo=dRwzL-ID1UQG