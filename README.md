# Bank-Desktop-Application-written-in-python-
#The project is Developed in python. Main objective of this Application is to develop a ATM Application which has two admin, one is user and another machine itself.
#best Bank Application by me
from getpass import getpass
data = {"1001":["simran","password",10000,'1601'], #format --> security question --> ddmm
       "1002":["ayushi","admin",15000,'1301'],
        "1003" : ["ayush","passwd",13000,'1902']
       }

while True:
    print("\n 1. Login \n 2. Signup \n 3. Forgot Passsword \n 4. Exit")
    ch = int(input("\n Choose any option from above : "))
    if ch == 1:
        accno = input("\n Enter your account number : ")
        if accno in data.keys():
            password = getpass("\n Enter your password : ")
            if data[accno][1] == password:
                print(f"Welcome {data[accno][0]}".center(80,"*"))
                while True:
                    print("\n 1. Credit \n 2. Debit \n 3. Change Passsword \n 4. Details \n 5. Logout")
                    ch = int(input("\n Choose any operation from above mentioned....."))
                    if ch == 1:
                        credit_amount = int(input("Enter the amount:"))
                        old_bal=data[accno][2]
                        new_bal=old_bal+credit_amount
                        data[accno][2]=new_bal
                        print('Credited Succesfully')
                        print('the new amount is :',new_bal)
                    elif ch == 2:
                        debit_amount = int(input("Enter the amount:"))
                        bal=data[accno][2]
                        if (bal!=0):
                            old=data[accno][2]
                            new=old-debit_amount
                            data[accno][2]=new
                            print(f'Rs.{debit_amount} has been deducted and left {new}\n Debit Successful!! ')
                        else:
                            print('You account has no balance')
                    elif ch == 3:
                        print('Note!!! your password must have 8 digits with minimum 1-1 SpecCh, Num, CapiAlpa and SmallAlpa')
                        password = input("Enter new password: ")
                        l,u,p,d = 0,0,0,0
                        if len(password)>=8:
                            for i in password:
                                if (i.islower()):
                                    l+=1
                                if (i.isupper()):
                                    u+=1
                                if (i.isdigit()):
                                    d+=1
                                if (i=='@'or i=='$' or i=='_' or i=='*' or i=='#' or i=='!' or i=='&' or i=='^' or i=='%'): 
                                    p+=1
                            if (l>=1 and u>=1 and p>=1 and d>=1 and l+p+u+d==len(password)):
                                print ("password valid!!")
                            else:
                                print ("password Invalid!!")
                            data[accno][1]=password
                            print("Password changed succesfully!!")
                        
                    elif ch == 4:
                        accno=input("Enter account no:")
                        x=data[accno][0]
                        y=data[accno][2]
                        print(f'Balance of {x} is :{y}')
                    elif ch == 5:
                        print("\n ThankYou!!!!")
                        break
                    else:
                        print("\n Please Choose an option from (1/2/3/4/5)")
            else:
                print("\n Password is not correct....Please Try again!!!")
        else:
            print("\n Please enter correct account number....")
    elif ch == 2:
        name = input("\n Enter your name : ")
        initial_bal = int(input("\n Enter your initial balance : "))
        l,u,p,d = 0,0,0,0
        #password = input("\n Enter your password : ")
        password = getpass("\n Enter your password : ")
        if len(password)>=8:
            for i in password:
                if (i.islower()):
                    l+=1
                if (i.isupper()):
                    u+=1
                if (i.isdigit()):
                    d+=1
                if (i=='@'or i=='$' or i=='_' or i=='*' or i=='#' or i=='!' or i=='&' or i=='^' or i=='%'): 
                    p+=1
        if (l>=1 and u>=1 and p>=1 and d>=1 and l+p+u+d==len(password)):
            print ("password valid!!")
        else:
            print ("password Invalid!!")
        dob = input("\n Enter your date of birth in ddmm format which is your security question : ")
        m = {(1,3,5,7,8,10,12):31,(2,):29,(4,6,9,11):30} # key --> months and values --> days
        date = dob[:2]
        month = dob[2:]
        #data={}
        sq = None
        for i in m:
            if int(month) in i:
                value = m[i]
                if int(date) >= 1 and int(date) <= value:
                    sq = dob
                else:
                    print("Incorrect date")
                break
        else:  #it will execute when the loop runs completely without any break 
            print("\n Incorrect date")
        if sq:
            accno = str(int(list(data.keys())[-1]) + 1)
            data[accno] = [name,password,initial_bal,sq]
            print("\n Your accnount number is : ",accno)
        else:
            print("\n Try again to signup your details were not valid......")
        
    elif ch == 3 :
        accno = input("\n Enter your account number : ")
        dob = input ("\n Enter your date of birth in ddmm format which is your security question :")
        if accno in data.keys():
            if dob == data[accno][3]:
                password = input("Enter new password:")
                l,u,p,d = 0,0,0,0
                if len(password)>=8:
                    for i in password:
                        if (i.islower()):
                            l+=1
                        if (i.isupper()):
                            u+=1
                        if (i.isdigit()):
                            d+=1
                        if (i=='@'or i=='$' or i=='_' or i=='*' or i=='#' or i=='!' or i=='&' or i=='^' or i=='%'): 
                            p+=1
                    if (l>=1 and u>=1 and p>=1 and d>=1 and l+p+u+d==len(password)):
                        print ("password valid!!")
                    else:
                        print ("password Invalid!!")
                    data[accno][1]=password
                    print("Password set succesfully!!")
        
        
    elif ch == 4:
        print("\n Thanks for using our services.....")
        break
    else:

        print("\n Please choose from 1/2/3/4.....")

