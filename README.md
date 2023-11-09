
# EXP NO 11: DATA BASE CONNECTIVITY USING  MYSQL AND PYTHON

### DATE: 25/10/23
### AIM: 
To create database connectivity and display the student table 
### Steps:

1. Install mysql,visual studio or python IDLE 3.12.
2. Create a student database and table in MySQL.
3. Pip install mysql-connector into python packages.
4. Write a python progarm to perform the following:
   a.) create a connection.
   b.) fetch data and store it in result set.
   c.) Display table rows.
   d.) Close the connection.
5. Run the program




### Program:

```
#PRGRAM TO CONNECT MYSQL AND PYTHON
#MENU DRIVEN PROGRAM

#To establish connection
import sys
import mysql.connector as mc
conn=mc.connect(host='localhost', user='root',passwd='1a2d8h12l',database='STUDENT')
cur=conn.cursor()

if conn.is_connected():
    print("Successfully connected to MySQL")
else:
    print("Could not connect to MySQL")

#INSERT INTO RECORD
def insert_rec():
    print("\nENTER RECORD DETAILS")
    refno=int(input("Enter register No: "))
    name=input("Enter Name: ")
    dept=input("Enter Department: ")
    yr=int(input("Enter Year of Study: "))
    R=(refno, name, dept, yr)
    qry="INSERT INTO STUDENT (REG_NO,NAME,DEPT,YEAR) VALUES (%s, %s, %s, %s)"
    cur.execute(qry,R)
    conn.commit()
    print("Record inserted successfully")
    return

#VIEW RECORD
def view_rec():
    print("\nFETCHING ALL RECORDS IN THE TABLE FOR VIEW")
    qry="SELECT * FROM STUDENT"
    cur.execute(qry)
    print("_______________________________________________")
    print("REGNO       NAME        DEPT       YEAR")
    print("_______________________________________________")
    data=cur.fetchall()
    for i in data:
        print(i[0],"\t",i[1],"\t",i[2],"\t",i[3])
    print("_______________________________________________")
    print("\nTotal no.of records = ",cur.rowcount)
    return

while(True):
    print("-"*60)
    print("           PYTHON-MYSQL CONNECTIVITY")
    print("         STUDENT RECORD MANIPULATION")
    print("-"*60)
    print("1. INSERT \n2. DISPLAY RECORD \n3. EXIT")
    ch=int(input("Enter the opertion's choice you want to perform[1-3] : "))
           
    if (ch==1):
           insert_rec()
    elif (ch==2):
        view_rec()
    else:
        print("Thank You !!")
        break
```

### Output:

![op-1](https://github.com/AnnBlessy/DBMS/assets/119477835/0bee54e1-971b-429b-a078-e64b23f62d96)
![op-2](https://github.com/AnnBlessy/DBMS/assets/119477835/429a8c9a-7a20-4b81-9734-a516a4541580)
![op-3](https://github.com/AnnBlessy/DBMS/assets/119477835/00b18fd9-b52a-4199-8740-45d278ce76e2)


### Result:
Thust the database is connected and data displayed sucessfully.
