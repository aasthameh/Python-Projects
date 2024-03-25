"""
This is a timed maths quiz game.
Players can choose the level of difficulty.
It has a total of 5 games. 
At the end, player gets their total time to complete the quiz and their total score : + 1 and -1 for every correct answer and wrong answer.
"""

#imports
import random
import time

# lets begin the game
# choose level of difficulty
while True:
    
  level = input("lets begin the game. choose the level of challenge- easy(e), medium(m), hard(h)").lower()
  if level == "e":
    x = 10
    a = 0
    print("get ready for easy level")
    break
  elif level == 'm':
    a = 20
    x = 50
    print("get ready for medium level")
    break
  elif level == 'h':
    a,x = 50,100
    print("get ready for hard level")
    break
  else:
    print("pls type e/m/h to choose")
    continue

# function to generate a random maths equation
def maths_eqtn():
  first_num=random.randint(a,x)
  second_num=random.randint(a,x)
  oper = ['-', '+', '*']
  choose_sign = random.choice(oper)
  eqtn = (str(first_num) + ' ' + choose_sign + ' ' + str(second_num) )
  result = eval(eqtn)
#   print(equation and result)
  return eqtn, result

  score=0

start_time = time.time()
for i in range (5):
    eqtn, result= maths_eqtn()

    print(f"solve {eqtn}")


    while True:
        user_answer = input("enter answer : ")
        try:

            if int(user_answer) == result:
                print(f'correct answer is {result}')
                score+=1
                break

            else:
                print('wrong, u lose a point')
                score-=1
                break

        except Exception as e:
            print("Please enter a valid integer.")
            continue




end_time = time.time()
total_time = end_time-start_time
print(f"ur total score is {score} in {round(total_time, 2)} seconds")
