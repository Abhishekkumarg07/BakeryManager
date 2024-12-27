# BakeryManagement
import mysql.connector
con=mysql.connector.connect(host='localhost',user='root',password='xyz')
cur=con.cursor()
cur.execute("create database if not exists items")
cur.execute("use items")
cur.execute("create table if not exists cs(sno int,products varchar(20),cost int)")
sql="select*from cs"
cur.execute(sql)
res=cur.fetchall()
if res==[]:
   cur.execute("insert into cs values(1,'Cake',50)")
   cur.execute("insert into cs values(2,'Pastry',20)")
   cur.execute("insert into cs values(3,'Milk',60)")
   cur.execute("insert into cs values(4,'Butter',20)")
   cur.execute("insert into cs values(5,'cheese',30)")
   con.commit()
cur.execute("create table if not exists vip(sno int,varieties varchar(20))")
sql="select*from vip"
cur.execute(sql)
res=cur.fetchall()
if res==[]:
    cur.execute("insert into vip values(1,'Vaniella')")
    cur.execute("insert into vip values(2,'Chocalate')")
    cur.execute("insert into vip values(3,'Strawberry')")
    cur.execute("insert into vip values(4,'Butter_scotch')")
    con.commit()
cur.execute("create table if not exists worker(Sno int,Name varchar(20),Salary int)")
sql="select*from worker"
cur.execute(sql)
res=cur.fetchall()
if res==[]:
    cur.execute("insert into worker values(1,'Mukesh',20000)")
    cur.execute("insert into worker values(2,'Ram',25000)")
    cur.execute("insert into worker values(3,'Dheeraj',19000)")
    cur.execute("insert into worker values(4,'Abhi',30000)")
    con.commit()
from datetime import datetime
print("______________________##CLASS 12TH CS PROJECT(083)##______________________")
print("__________________________________________________________________________")   
print("|.....................@@@@@@@@@@WELCOME@@@@@@@@@@.........................|")
print("|.....................@@@@@@@@@@@@@TO@@@@@@@@@@@@.........................|")
print("|........................BAKERY MANAGEMENT SYSTEM.........................|")
print("|........................SESSION:2022-2023................................|")
print("___________________________________________________________________________")
ch=''
while ch!='N' or ch!='n':
     print("\n\nPLEASE CHOOSE \n1 FOR ADMIN \n2 FOR COSTUMER\n3 FOR EXIT:\n")
     choice=int(input("ENTER YOUR CHOICE"))
     if choice==3:
        break
     if choice==1:
      admin=input("USERNAME:")
      if admin in['abhi','ram']:
        password=int(input("ENTER PASSWORD"))
        if password==1234:
            print("*************HELLO SIR,YOU LOGGED IN AS ADMIN SUCCESSFUL**********")
            print("_____________________________________________________________________________")
            print("Press 1 to add Item in the shop...")
            print("Press 2 to see items in the shop..")
            print("press 3 to update cost of any item...")
            print("press 4 to add varieties of cake in shop..")
            print("press 5 to add worker in shop..")
            print("press 6 to see workers....")
            print("press 7 to update salary of any workers...")
            c=int(input('Enter your choice'))
            if c==1:
                  def add():
                       sno=int(input("Enter sno"))
                       product1=input("Enter product name")
                       cost=int(input("Enter cost"))
                       d1=(sno,product1,cost)
                       s1='insert into cs values(%s,%s,%s)'
                       cur.execute(s1,d1)
                       con.commit()
                       print('...............................................////////////////ITEM ADDED SUCCESFULLY/////////////////.....................................')
                  add()
            elif c==2:
                def items():
                    print("ITEMS IN THE SHOP")
                    sql="select*from cs"
                    cur.execute(sql)
                    res=cur.fetchall()
                    t=(['serial_no','products','cost'])
                    for serial_no,products,cost in res:
                        print(serial_no,":","\t",products,":\t\t",'cost',cost)
                items()
            elif c==3:
                 def money():
                    sno=input("ENTER THE SNO OF PRODUCT")
                    n_cost=input("ENTER THE RUPEES TO BE ADDED:")
                    cur.execute("update cs set cost=cost+"+n_cost+" where sno="+sno+';')
                    con.commit()
                    print("TABLE AFTER UPDATION:")
                    sq="select*from cs"
                    cur.execute(sq)
                    res=cur.fetchall()
                    t=(['sno','products','cost'])
                    for sno,products,cost in res:
                        print(sno,":","\t",products,":","\t",'Cost',cost)
                 money()
            elif c==4:
                def variety():
                    sno=input("ENTER SNO:")
                    varieties=input("Enter variety")
                    d2=(sno,varieties)
                    s2='insert into vip values(%s,%s)'
                    cur.execute(s2,d2)
                    con.commit()
                variety()
            elif c==5:
                def ad():
                    sno=int(input("ENTER SNO:"))
                    emp=input("ENTER NAME:")
                    salary=int(input("ENTER THE SALARY:"))
                    dx=(sno,emp,salary)
                    sy='insert into worker values(%s,%s,%s)'
                    cur.execute(sy,dx)
                    con.commit()
                    print('.........................................///////////////////////////WORKERS ARE UPDATED//////////////////..........................................')
                ad()
            elif c==6:
                def workers():
                    print("WORKERS IN THE SHOP")
                    sql="select*from worker"
                    cur.execute(sql)
                    res=cur.fetchall()
                    t=(['serial_no','name','salary'])
                    for serial_no,name,salary in res:
                        print(serial_no,":","\t",name,":","\t",'cost',salary)
                workers()
            elif c==7:
                def up():
                    print("CHOOSE 1 TO INCREASE THE SALARY")
                    print("CHOOSE 2 TO DECREASE")
                    name=input("ENTER THE NAME OF EMPLOYEE")
                    n_salary=input("ENTER THE RUPEES TO BE ADDED:")
                    sig=int(input("ENTER CHOICE(1/2):"))
                    if sig==1:
                        cur.execute("update worker set salary=salary+"+n_salary+" where name="+name+';')
                        con.commit()
                        print("TABLE AFTER UPDATION")
                        sq="select*from worker"
                        cur.execute(sq)
                        res=cur.fetchall()
                        t=(['sno','name','salary'])
                        for sno,name,salary in res:
                              print(sno,":","\t",name,":","\t",salary)
                    if sig==2:
                        cur.execute("update worker set salary=salary-"+n_salary+" where name="+name+';')
                        con.commit()
                        print("TABLE AFTER UPDATION")
                        sq="select*from worker"
                        cur.execute(sq)
                        res=cur.fetchall()
                        t=(['sno','name','salary'])
                        for sno,name,salary in res:
                            print(sno,":","\t",name,":","\t",salary)
                up()
            else:
                print("SORRY..YOU HAVE ENTERED THE WRONG INPUT FROM 1 TO 7")
        else:
           print("\t\t\t\t\t\t**********************WRONG PASSWORD**********************\t\t\t\t\t\t")
      else:
          print("\t\t\t\t\t\t\t**********************WRONG USER NAME*********************\t\t\t\t\t\t\t")
     elif choice==2:
        name=input("ENTER YOUR NAME:")
        phone=input("ENTER YOUR PHONE NUMBER:")
        if len(phone)==10:
          print("WHAT DO YOU LIKE TO ORDER")
          sql="select*from cs"
          cur.execute(sql)
          res=cur.fetchall()
          t=(['serial_no','products','cost'])
          for serial_no,products,cost in res:
            print(serial_no,":","\t",products,":","\t",'cost',cost)
          sql='select sno from cs'
          cur.execute(sql)
          res=cur.fetchall()
          print(res)
          l=[]
          for i in range(len(res)):
                l.append(res[i][0])
          print(l)
          d=int(input("ENTER YOUR SERIAL NO OF THE ITEM TO BUY:"))
          if d==1:
             def items():
                    print("WHICH CAKE DO YOU WANT?")
                    kl="select*from vip"
                    cur.execute(kl)
                    srh=cur.fetchall()
                    f=(['sno','varieties'])
                    for sno,varieties in srh:
                        print(sno,":","\t\t",varieties)
                    print("CHOOSE WHICH CAKE DO YOU WANT?")
                    ck=int(input("ENTER CHOICE"))
                    if ck==ck:
                        print('HOW MUCH YOU NEED:')
                        qty=int(input("ENTER QTY:"))
                        print("YOU HAVE SUCCESSFULLY ORDERED YOUR CAKE")
                        cur.execute("select*from cs where products='cake'"';')
                        for i in cur:
                            A=i[2]
                        print("TOTAL AMOUNT:",qty*A)
                        print("\n")
                        print("....................................................................................................................")
                        print("YOUR BILL")
                        print("____________________________________________________________________________________________________________________")
                        print("COSTUMERS NAME:",name)
                        print("CONTACT NO:",phone)
                        print("NO OF CAKES:",qty)
                        print("TOTAL AMOUNT:",qty*A)
                        print("@@@@@@@@@@@@@@@@@@@@THANK YOU FOR ORDERING THE ITEM@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@")
                        print("\t\t\t\t\t\t\t\t\t\t\tDATE:",datetime.now())   
             items()
          elif d==2:
                print("HOW MUCH PASTRY DO YOU WANT:")
                past=int(input("ENTER YOUR CHOICE :"))
                print("YOU HAVE SUCCESSFULLY ORDERED",past,"pastry")
                cur.execute("select*from cs where products='pastry'"';')
                for i in cur:
                    c=i[2]
                print("TOTAL AMOUNT=",past*c)
                print("\n")
                print("....................................................................................................................")
                print("YOUR BILL")
                print("____________________________________________________________________________________________________________________")
                print("COSTUMERS NAME:",name)
                print("CONTACT NO:",phone)
                print("NO OF PASTRY:",past)
                print("TOTAL AMOUNT:",past*c)
                print("@@@@@@@@@@@@@@@@@@@@THANK YOU FOR ORDERING THE ITEM@@@@@@@@@@@@@@@@@@@@")
                print("\t\t\t\t\t\t\t\t\t\t\tDATE:",datetime.now())
          elif d==3:
                print("HOW MUCH LITRES OF MILK DO YOU NEED?")
                mlk=int(input("ENTER HOW MUCH LITRES "))
                print("YOU HAVE SUCCESSFULLY ORDERED",mlk,"l of milk")
                cur.execute("select*from cs where products='milk'"';')
                for i in cur:
                    c=i[2]
                print("TOTAL AMOUNT=",mlk*c)
                print("\n")
                print("....................................................................................................................")
                print("YOUR BILL")
                print("____________________________________________________________________________________________________________________")
                print("COSTUMERS NAME:",name)
                print("CONTACT NO:",phone)
                print("QUANTITY OF MILK:",mlk)
                print("TOTAL AMOUNT:",mlk*c)
                print("@@@@@@@@@@@@@@@@@@@@THANK YOU FOR ORDERING THE ITEM@@@@@@@@@@@@@@@@@@@@")
                print("\t\t\t\t\t\t\t\t\t\t\tDATE:",datetime.now())
          elif d==4:
                print("HOW MANY PACKETS(20g) OF BUTTER DO YOU WANT?")
                but=int(input("ENTER"))
                print("YOU HAVE SUCCESSFULLY ORDERED",but,"PACKETS OF BUTTER")
                cur.execute("select*from cs where products='butter'"';')
                for i in cur:
                    c=i[2]
                print("TOTAL AMOUNT=",but*c)
                print("\n")
                print("....................................................................................................................")
                print("YOUR BILL")
                print("____________________________________________________________________________________________________________________")
                print("COSTUMERS NAME:",name)
                print("CONTACT NO:",phone)
                print("NO OF butter:",but)
                print("TOTAL AMOUNT:",but*c )
                print("@@@@@@@@@@@@@@@@@@@@THANK YOU FOR ORDERING THE ITEM@@@@@@@@@@@@@@@@@@@@")
                print("\t\t\t\t\t\t\t\t\t\t\tDATE:",datetime.now())
          elif d==4:
                print("HOW MUCH CHEESE(IN KG) DO YOU WANT")
                chs=int(input("ENTER YOUR CHOICE"))
                print("YOU HAVE SUCCESSFULLY ORDERED",chs,"KG OF CHEESE")
                cur.execute("select*from cs where products='cheese'"';')
                for i in cur:
                    c=i[2]
                print("TOTAL AMOUNT=",chs*c)
                print("\n")
                print("....................................................................................................................")
                print("YOUR BILL")
                print("____________________________________________________________________________________________________________________")
                print("COSTUMERS NAME:",name)
                print("CONTACT NO:",phone)
                print("NO OF CHEESE:",chs)
                print("TOTAL AMOUNT:",chs*c)
                print("@@@@@@@@@@@@@@@@@@@@THANK YOU FOR ORDERING THE ITEM@@@@@@@@@@@@@@@@@@@@")
                print("\t\t\t\t\t\t\t\t\t\t\tDATE:",datetime.now())
          elif d in l:
                qty=int(input("ENTER QTY"))
                print("YPU HAVE SUCCESSFULLY ORDERED YOUR SELECTED ITEM!!!\t:")
                cur.execute("select*from cs where sno="+str(d))
                for i in cur:
                    L=i[2]
                print("TOTAL AMOUNT=",qty*L)
                print("\n")
                print("....................................................................................................................")
                print("YOUR BILL")
                print("____________________________________________________________________________________________________________________")
                print("COSTUMERS NAME:",name)
                print("CONTACT NO:",phone)
                print("QUANTITY:",qty)
                print("TOTAL AMOUNT:",qty*L)
                print("@@@@@@@@@@@@@@@@@@@@THANK YOU FOR ORDERING THE ITEM@@@@@@@@@@@@@@@@@@@@")
                print("\t\t\t\t\t\t\t\t\t\t\tDATE:",datetime.now())
          else:
             print("WRONG INPUT")
        else:
          print("\t\t\t*************************ENTER VAILD PHONE NUMBER**********************************\t\t\t")
     else:
        print("\t\t\t\t\t\t\t\t\t\t\t**********************WRONG PASSWORD**********************\t\t\t\t\t\t\t\t\t\t\t\t\t\t")
ch=input("DO YOU WANT TO CONTINUE(Y/N)?")
if ch=='n':
      exit()
#  bank management
import pickle
import os
import pathlib
class Account :
    accNo = 0
    name = ''
    deposit=0
    type = ''
    
    def createAccount(self):
        self.accNo= int(input("Enter the account no : "))
        self.name = input("Enter the account holder name : ")
        self.type = input("Ente the type of account [C/S] : ")
        self.deposit = int(input("Enter The Initial amount(>=500 for Saving and >=1000 for current"))
        print("\n\n\nAccount Created")
    
    def showAccount(self):
        print("Account Number : ",self.accNo)
        print("Account Holder Name : ", self.name)
        print("Type of Account",self.type)
        print("Balance : ",self.deposit)
    
    def modifyAccount(self):
        print("Account Number : ",self.accNo)
        self.name = input("Modify Account Holder Name :")
        self.type = input("Modify type of Account :")
        self.deposit = int(input("Modify Balance :"))
        
    def depositAmount(self,amount):
        self.deposit += amount
    
    def withdrawAmount(self,amount):
        self.deposit -= amount
    
    def report(self):
        print(self.accNo, " ",self.name ," ",self.type," ", self.deposit)
    
    def getAccountNo(self):
        return self.accNo
    def getAcccountHolderName(self):
        return self.name
    def getAccountType(self):
        return self.type
    def getDeposit(self):
        return self.deposit
    

def intro():
    print("\t\t\t\t**********************")
    print("\t\t\t\tBANK MANAGEMENT SYSTEM")
    print("\t\t\t\t**********************")

    print("\t\t\t\tBrought To You By:")
    print("\t\t\t\tprojectworlds.in")
    input()



def writeAccount():
    account = Account()
    account.createAccount()
    writeAccountsFile(account)

def displayAll():
    file = pathlib.Path("accounts.data")
    if file.exists ():
        infile = open('accounts.data','rb')
        mylist = pickle.load(infile)
        for item in mylist :
            print(item.accNo," ", item.name, " ",item.type, " ",item.deposit )
        infile.close()
    else :
        print("No records to display")
        

def displaySp(num): 
    file = pathlib.Path("accounts.data")
    if file.exists ():
        infile = open('accounts.data','rb')
        mylist = pickle.load(infile)
        infile.close()
        found = False
        for item in mylist :
            if item.accNo == num :
                print("Your account Balance is = ",item.deposit)
                found = True
    else :
        print("No records to Search")
    if not found :
        print("No existing record with this number")

def depositAndWithdraw(num1,num2): 
    file = pathlib.Path("accounts.data")
    if file.exists ():
        infile = open('accounts.data','rb')
        mylist = pickle.load(infile)
        infile.close()
        os.remove('accounts.data')
        for item in mylist :
            if item.accNo == num1 :
                if num2 == 1 :
                    amount = int(input("Enter the amount to deposit : "))
                    item.deposit += amount
                    print("Your account is updted")
                elif num2 == 2 :
                    amount = int(input("Enter the amount to withdraw : "))
                    if amount <= item.deposit :
                        item.deposit -=amount
                    else :
                        print("You cannot withdraw larger amount")
                
    else :
        print("No records to Search")
    outfile = open('newaccounts.data','wb')
    pickle.dump(mylist, outfile)
    outfile.close()
    os.rename('newaccounts.data', 'accounts.data')

    
def deleteAccount(num):
    file = pathlib.Path("accounts.data")
    if file.exists ():
        infile = open('accounts.data','rb')
        oldlist = pickle.load(infile)
        infile.close()
        newlist = []
        for item in oldlist :
            if item.accNo != num :
                newlist.append(item)
        os.remove('accounts.data')
        outfile = open('newaccounts.data','wb')
        pickle.dump(newlist, outfile)
        outfile.close()
        os.rename('newaccounts.data', 'accounts.data')
     
def modifyAccount(num):
    file = pathlib.Path("accounts.data")
    if file.exists ():
        infile = open('accounts.data','rb')
        oldlist = pickle.load(infile)
        infile.close()
        os.remove('accounts.data')
        for item in oldlist :
            if item.accNo == num :
                item.name = input("Enter the account holder name : ")
                item.type = input("Enter the account Type : ")
                item.deposit = int(input("Enter the Amount : "))
        
        outfile = open('newaccounts.data','wb')
        pickle.dump(oldlist, outfile)
        outfile.close()
        os.rename('newaccounts.data', 'accounts.data')
   

def writeAccountsFile(account) : 
    
    file = pathlib.Path("accounts.data")
    if file.exists ():
        infile = open('accounts.data','rb')
        oldlist = pickle.load(infile)
        oldlist.append(account)
        infile.close()
        os.remove('accounts.data')
    else :
        oldlist = [account]
    outfile = open('newaccounts.data','wb')
    pickle.dump(oldlist, outfile)
    outfile.close()
    os.rename('newaccounts.data', 'accounts.data')
    
        
# start of the program
ch=''
num=0
intro()

while ch != 8:
    #system("cls");
    print("\tMAIN MENU")
    print("\t1. NEW ACCOUNT")
    print("\t2. DEPOSIT AMOUNT")
    print("\t3. WITHDRAW AMOUNT")
    print("\t4. BALANCE ENQUIRY")
    print("\t5. ALL ACCOUNT HOLDER LIST")
    print("\t6. CLOSE AN ACCOUNT")
    print("\t7. MODIFY AN ACCOUNT")
    print("\t8. EXIT")
    print("\tSelect Your Option (1-8) ")
    ch = input()
    #system("cls");
    
    if ch == '1':
        writeAccount()
    elif ch =='2':
        num = int(input("\tEnter The account No. : "))
        depositAndWithdraw(num, 1)
    elif ch == '3':
        num = int(input("\tEnter The account No. : "))
        depositAndWithdraw(num, 2)
    elif ch == '4':
        num = int(input("\tEnter The account No. : "))
        displaySp(num)
    elif ch == '5':
        displayAll();
    elif ch == '6':
        num =int(input("\tEnter The account No. : "))
        deleteAccount(num)
    elif ch == '7':
        num = int(input("\tEnter The account No. : "))
        modifyAccount(num)
    elif ch == '8':
        print("\tThanks for using bank managemnt system")
        break
    else :
        print("Invalid choice")
    
    ch = input("Enter your choice : ")
    
