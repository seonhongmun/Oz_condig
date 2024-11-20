balance = 1000
print(f"현재 금액: {balance}원")
receipts = []

while True:
    num = input("사용하실 기능을 선택해주세요 (1:입금, 2:출금, 3:영수증보기, 4:종료)")
    if num == "1":
        #입금기능  
        deposit_amount = int(input("입금할 금액을 입력해주세요 : ")) #3000 문자형태 "3000" 그렇기에 int()추가 
        balance += deposit_amount   #balance에 입금한 금액을 더하고 삽입한다.
        receipts.append(("입금", deposit_amount ,balance))
        print(f'입금이 완료되었습니다. 입금하신 금액은 {deposit_amount}원이고, 계좌 총 잔액은 {[balance]}원 입니다.')
    elif num == "2":
        #출금기능  
        withdraw_amount  = int(input("출금할 금액을 입력해주세요 : ")) #출금금액 input
        withdraw_amount = min(balance, withdraw_amount) #
        balance -= withdraw_amount   #balance에 입금한 금액을 더하고 삽입한다.
        receipts.append(("출금", withdraw_amount ,balance))
        print(f'출금이 완료되었습니다 출금하신 금액은 {withdraw_amount}원이고, 계좌 총 잔액은 {[balance]}원 입니다.')
    elif num == "3" :
        #영수증
        print("모든 거래 내역을 보여드립니다.", receipts)
    elif num == "4" :
        #종료
        break
print("프로그램을 종료합니다.")