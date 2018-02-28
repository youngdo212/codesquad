# codesquad
import random

def createAnswer():
    result = []
    num = ['0','1','2','3','4','5','6','7','8','9']
    for i in range(3):
        select = random.choice(num)
        result.append(select)
        num.remove(select)
    return ''.join(result)

def checkStrike(answer, number):
    result = 0
    for i in range(3):
        if number[i] == answer[i]:
            result += 1
    return result
    
def checkBall(answer, number):
    result = 0
    for i in range(3):
        if number[i] == answer[(i+1)%3]:
            result += 1
        if number[i] == answer[(i+2)%3]:
            result += 1
    return result

def printOut(strike, ball):
    if strike == 0 and ball == 0:
        print("낫싱")
    elif ball == 0:
        print(strike, "스트라이크")
    elif strike == 0:
        print(ball, "볼")
    else:
        print(strike, "스트라이크", ball, "볼")

def baseballGame(answer):
    while True:
        number = input("숫자를 입력해주세요 ex)123 : ")
        printOut(checkStrike(answer, number), checkBall(answer, number))
        if checkStrike(answer, number) == 3:
            break
    print("3개의 숫자를 모두 맞히셨습니다! 게임 종료")
    
answer = createAnswer()
baseballGame(answer)
