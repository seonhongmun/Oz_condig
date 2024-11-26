## for문이란?
프로그래밍 언어에서 반복되는 작업을 간단하게 처리하기 위해서 사용되는 기능
for문 문법과 주의사항(콜론, 들여쓰기)

## 2. for문으로 만들어보기
# for 변수 in range(횟수):
#   print()

for i in range(5):
    print("반복")
반복
반복
반복
반복
반복

## 3. for문의 흐름 확인

for i in range(5):
    print("반복", i)
반복 0
반복 1
반복 2
반복 3
반복 4


## 4. for문에서 range() 함수 활용하기
for i in range(4,10): # 4 ~ 10까지만 반복
    print("반복", i)

for i in range(4,10,2): # 4 ~ 10까지 2를 뛰며 반복
    print("반복", i)

for i in range(10,3,-1): # 10 ~ 3 까지 역순으로 반복
    print("반복", i)

for i in reversed(range(10)): # 10 ~ 0에서 역순으로 반복
    print("반복", i)
반복 9
반복 8
반복 7
반복 6
반복 5
반복 4
반복 3
반복 2
반복 1
반복 0


#5. for문에서 시퀀스 객체로 반복하기
과일 = ["사과", "배", "딸기", "수박"]

    # for i in 과일:
    #     print(i)

    # for i in "닥스훈트":
    #     print(i,end="")


for i in reversed("닥스훈트"):
    print(i,end="")
트훈스닥


## 6 예제로 for문
# 문제 : 절대값 정수가 담긴 정수 변수와 그 정수의 부호를 차례로 담은 부호 변수가 있다.
# 두 변수를 이용해 실제 정수의 합을 구하세요 (True : 양수, False : 음수)

정수 = [10,5,8]
부호 = [True, False, True]

합 = 0

# for i in range(3):

13
