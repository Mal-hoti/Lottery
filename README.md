# Lottery
My python code of a lottery game

````````
import random
import time
import math
max_num,min_num=59,1
input_is_max = True
length_of_lottery = 6
list_of_num = []
seperated_numbers = []
print('Welcome to lottery. pick numbers form 1-49 and at the end write your bonus ball')


while len(list_of_num) <=length_of_lottery :
    
    random_num = random.randint(min_num,max_num)
    if random_num not in list_of_num: 
        list_of_num.append(random_num)
    else:
        continue

def write_numbers():
    global seperated_numbers
    global length_of_lottery
    global range_num
    max_num,min_num=49,1
    
    range_num = (max_num-min_num) + 1
    
    try:
        user_input= input("\nEnter your {} numbers using a comma to seperate them:\n".format(length_of_lottery))
        seperated_number = user_input.split(',')
        seperated_numbers = list(map(int, seperated_number))   #converts the strong into integers in the list
    except:
        print("An error has occured, please try again!")
        write_numbers()
    
    
    for i in range(len(seperated_numbers)):
        if seperated_numbers[i] <=0 or seperated_numbers[i]>49:
            print('It has to be within',min_num,'-', max_num)
            write_numbers()


            
    if len(seperated_numbers) != len(set(seperated_numbers)):
       print("You cant have matching numbers")
       write_numbers()
                                     
    if len(seperated_numbers) != length_of_lottery:
        
        print('You have to write',length_of_lottery,'numbers!')
        write_numbers()
    else:
        print()

write_numbers()

list_of_num.sort()

matching = set(list_of_num).intersection(set(seperated_numbers))   # compares the two list an prints the similar values only

print("\nLottery numbers are...\n")
time.sleep(0.5)
print("/".join(map(str,list_of_num)))
time.sleep(2)
print("\nYour numbers are...\n")
time.sleep(0.5)
print("/".join(map(str,seperated_numbers)))
time.sleep(2)

    
print("\nYou have got" , len(matching) , "matching!!")
if len(matching) == 0:
    print("Unlucky")
elif len(matching) == 1:
    print("Matching number...\n" + "/".join(map(str,matching)))
else:
    print("Matching numbers...\n" + "/".join(map(str,matching)))


print('The probabalitiy of having that combination is 1 in',int((math.factorial(range_num)/(math.factorial(length_of_lottery)*math.factorial(range_num-length_of_lottery)))))

time.sleep(2.5)
play_again = input("\nDo you want to play again?\n1) Yes\n2) No")
if play_again == 1:
    write_numbers()
else:
    quit()
```

      

        






      

