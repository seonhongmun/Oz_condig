## if문 
1. if문이란?
특정 조건일때 코드를 실행하는 문법
2. if문 문법과 주의사항(콜론, 들여쓰기)
if문의 조건 이후의 if문에 속한 코드는 들여쓰기를 통해 표시한다.
들여쓰기를 무시했을 때 오류가 발생.
콜론을 빼먹지 않도록 주의한다.


## 2. if문 문법과 주의사항 (콜론, 들여쓰기)
개수 = int(input("붕어빵 몇개 사실건가요?"))

if 개수 > 3 :
    print("개당 1800원입니다.")
    print(f'총 금액은 {개수 * 1800}원 입니다.')
붕어빵 몇개 사실건가요?5
개당 1800원입니다.
총 금액은 9000원 입니다.


## 3. if문의 흐름(작동원리)
# 코드는 위에 아래 순서대로 작동한다.

# 2)개수라는 변수에 담은 1)입력을 받음
개수 = int(input("붕어빵 몇개 사실건가요?"))
# 3) 개수 변수가 있어 값을 확인 하게됨  True/False
if 개수 > 3 :
    print("개당 1800원입니다.")
if 개수 <= 3:
    print("개당 2000원입니다.") # 2를 입력했을경우 위에 if문은 해당이 되지 않기에 brake
붕어빵 몇개 사실건가요?2
개당 2000원입니다.


## 4. if 중첩문

의문의_숫자 = 10

if 의문의_숫자 > 5 :
    if 의문의_숫자 < 15:
        print("의문의_숫자는 5보다 크고 15보다 작습니다.")
의문의_숫자는 5보다 크고 15보다 작습니다.


## 5. if~else 문법과 주의사항 (콜론, 들여쓰기)
# Ture 일때는 if문 안에 작성된 코드가 실행
# False 일때는 else문 안에 작성된 코드가 실행
개수 = int(input("붕어빵 몇개 사실건가요?"))

if 개수 > 3 :
    print("개당 1800원입니다.")

else :
    print("개당 2000원입니다.")
붕어빵 몇개 사실건가요?3
개당 2000원입니다.


## 6. if~else문 흐름 (주의사항)
개수 = int(input("붕어빵 몇개 사실건가요?"))

if 개수 > 3 :
    print("개당 1800원입니다.")

else :
    print("개당 2000원입니다.")


## 7. 조건문 조건(True, False)
# True
if True:
    print("True입니다.")
else :
    print("False입니다.")

# False
if False:
    print("True입니다.")
else :
    print("False입니다.")

# None
if None:
    print("True입니다.")
else :
    print("False입니다.")

# 0 False
if 0:
    print("True입니다.")
else :
    print("False입니다.")

# 1 True
if 1:
    print("True입니다.")
else :
    print("False입니다.")


# 1.1 모든 문자열은 True
if 1.1:
    print("True입니다.")
else :
    print("False입니다.")

# 2.1 모든 문자열은 True
if 2.1:
    print("True입니다.")
else :
    print("False입니다.")

# "" 아무값이 없음
if "":
    print("True입니다.")
else :
    print("False입니다.")

# not True. Fasle
if not True:
    print("True입니다.")
else :
    print("False입니다.")
 

True입니다.
False입니다.
False입니다.
False입니다.
True입니다.
True입니다.
True입니다.
False입니다.
False입니다.


## 8. 조건식 여러개 설정하기

a,b = 10, 20

if a == 10 and b == 30:
    print("True입니다.")
else :
    print("False입니다.")


if a == 10 or b == 30:
    print("True입니다.")
else :
    print("False입니다.")

if a >= 10 and a <=20:
    print("10보다 크고 20보다 작습니다.")


if 10 <= a < 20:
    print("10보다  20보다 작습니다.")

False입니다.
True입니다.
10보다 크고 20보다 작습니다.
10보다  20보다 작습니다.


#9. elif ~ if문

맛 = input("붕어빵 맛을 골라주세요 (팥, 슈크림, 잡채)")

if 맛 == "팥":
    print(f'{맛}을 선택하셨습니다.')
elif 맛 == "슈크림" :
    print(f"{맛}을 선택하셨습니다.")
else :
    print(f'{맛}을 선택하셨습니다.')
붕어빵 맛을 골라주세요 (팥, 슈크림, 잡채)잡채
잡채을 선택하셨습니다.


# 10. 예제로 if문 익혀보기
# 문제 : 단어 a의 가운데 글자를 반환하는 코드
# 조건 : 단어의 길이가 짝수라면 가운데 두 글자를 출력하면 된다.
# a = ("abcde")
# b = ("qwer")

a = input("단어를 입력하세요 : ")

가운데 = int(len(a) / 2)


단어를 입력하세요 : abcdeerf
de