import mysql.connector 
conn = mysql.connector.connect(
    host="localhost",
    user="root",
    password="100210",
    database="odd_eve")
cursor=conn.cursor()

freq=1 
import random
name=input('Enter your name')
while True:
    print('type 1, to get the number of fours')
    print('type 2, to get the number of sixes')
    print('type 3, to get the number of tens')
    print('type 4, to get the number of bowls faced')
    print('type 5, to get the net score')
    print('type 6, to get the best match')
    print('type 7, to get the number of wins/loses')
    print('type 8, to get a record deleted')
    print('type 9, to get the name changed')
    print('type 10, to continue')
    print('type 11, to exit')
    p=int(input('enter your choice'))
    if p==10:
        freq+=1 
        x1=input('This is a program for odd eve game')
        x2=input('Follow the instructions to operate a fluid game')
        x3=input('proceed to toss')
        x4=int(input('Enter your guess, in numerical from 1 to 2'))
        x5=random.randint(1,2)
        if x4==x5:
            print('You won the toss!')
            x6=int(input('press 1 for batting and 2 for bowling'))
            if x6==1:
                entry=1
                #print('The code is running')
                x9=0
                print('Enter your guess from 1 to 10') #Batting 1
                counter_1=0 #for number of sixes
                counter_2=0 #for number of tens
                counter_3=0 #for number of fours
                mt_list_1=[]
                while True:
                    x7=int(input())
                    mt_list_1.append(x7)
                    #for i in mt_list_1:
                    if x7==6:
                        counter_1+=1 
                    elif x7==10:
                        counter_2+=1
                    elif x7==4:
                        counter_3+=1
                    x8=random.randint(1,10)
                    print(x8)
                    if x8==x7:
                        print('You are out!')
                        break
                    else:
                        x9+=x7
                data_1=(x9, counter_1, counter_3, counter_2, len(mt_list_1), name, entry, freq)
                sql='insert into odd_eve (runs_made, sixes, fours, tens, bowls_faced, name, entry, frequency) values (%s, %s, %s, %s, %s, %s, %s, %s)'
                cursor.execute(sql, data_1)
                conn.commit()
                print("final score is:", x9)
                print('you are defending', x9)
                print('proceed to bowl')
                t1=0
                while t1<x9:
                    y1=int(input())
                    y2=random.randint(1,10)
                    print(y2)
                    t1+=y2
                    if y1==y2:
                        print('computer is out as its score is:', t1)
                        print('You won the game')
                        sql='update odd_eve set result="won"'
                        cursor.execute(sql)
                        conn.commit()
                        break
                    elif t1>x9:
                        print('you lost the game')
                        print('computer score is:', t1)
                        sql='update odd_eve set result="lose"'
                        cursor.execute(sql)
                        conn.commit()
                        break
            else:
                entry=2
                print('PC proceeds to bat')
                x12=0
                while True:
                    x10=int(input())
                    x11=random.randint(1,10)
                    print(x11)
                    if x11==x10:
                        print('computer is out')
                        break
                    else:
                        x12+=x11
                print('final score of the computer is:', x12)
                print('to win you have to make', x12)
                input('proceed to bat')
                t1=0
                counter_4=0 
                counter_5=0 
                counter_6=0 
                mt_list_2=[]
                while t1<x12:
                    
                    y1=int(input()) #batting 2 
                    mt_list_2.append(y1)
                    #for i in mt_list_2:
                    if y1==4:
                        counter_4+=1 
                    elif y1==6 :
                        counter_5+=1 
                    elif y1==10 :
                        counter_6+=1
                    y2=random.randint(1,10)
                    print(y2)
                    t1+=y1
                    if y1==y2:
                        print('you are out as your score is:', t1)
                        print('You lost the game')
                        sql='update odd_eve set result="lose"'
                        cursor.execute(sql)
                        conn.commit()
                        break
                    elif t1>x12:
                        print('you won the game')
                        print('your score is:', t1)
                        sql='update odd_eve set result="won"'
                        cursor.execute(sql)
                        conn.commit()
                        break
                data_2=(t1, counter_5, counter_4, counter_6, len(mt_list_2), name, entry, freq)
                sql='insert into odd_eve (runs_made, sixes, fours, tens, bowls_faced, name, entry, frequency) values (%s, %s, %s, %s, %s, %s, %s, %s)'
                cursor.execute(sql, data_2)
                conn.commit()
        else:
            print('You lost the toss')
            x13=random.randint(1,2)
            if x13==1:
                entry=3
                print('PC chooses batting')
                print('Proceed to bowl')
                x14=0
                while True:
                    x15=int(input())
                    x16=random.randint(1,10)
                    print(x16)
                    if x15==x16:
                        print('computer is out')
                        break
                    else:
                        x14+=x16
                print('computer final score:', x14)
                print('to win you have to make', x14)
                input('proceed to bat')
                t1=0
                counter_7=0 
                counter_8=0 
                counter_9=0 
                mt_list_3=[]
                while t1<x14:
                    y1=int(input()) #batting 3
                    
                    y2=random.randint(1,10)
                    mt_list_3.append(y1)
                    #for i in mt_list_3:
                    if y1==4:
                        counter_7+=1 
                    elif y1==6:
                        counter_8+=1 
                    elif y1==10: 
                        counter_9+=1
                    print(y2)
                    t1+=y1
                    if y1==y2:
                        print('you are out as your score is:', t1)
                        print('You lost the game')
                        sql='update odd_eve set result="lose"'
                        cursor.execute(sql)
                        conn.commit()
                        break
                    elif t1>x14:
                        print('you won the game')
                        print('your score is:', t1)
                        sql='update odd_eve set result="won"'
                        cursor.execute(sql)
                        conn.commit()
                        break
                data_3=(t1, counter_8, counter_7, counter_9, len(mt_list_3), name, entry, freq)
                sql='insert into odd_eve (runs_made, sixes, fours, tens, bowls_faced, name, entry, frequency) values (%s, %s, %s, %s, %s, %s, %s, %s)'
                cursor.execute(sql, data_3)
                conn.commit()
            else:
                entry=4
                print('computer chooses bowling')
                print('PC proceeds to bowl')
                x17=0
                counter_10=0 
                counter_11=0 
                counter_12=0 
                mt_list_4=[]
                while True:
                    x18=int(input()) #Batting 4
                               
                    x19=random.randint(1,10)
                    mt_list_4.append(x18)
                    #for i in mt_list_4:
                    if x18==4:
                        counter_10+=1 
                    elif x18==6:
                        counter_11+=1 
                    elif x18==10:
                        counter_12+=1
                    print(x19)
                    if x18==x19:
                        print('You are out!')
                        break
                    else:
                        x17+=x18
                data_4=(x17, counter_11, counter_10, counter_12, len(mt_list_4), name, entry, freq)
                sql='insert into odd_eve (runs_made, sixes, fours, tens, bowls_faced, name, entry, frequency) values (%s, %s, %s, %s, %s, %s, %s, %s)'
                cursor.execute(sql, data_4)
                conn.commit()
                print('Your total score is:', x17)
                print('You are defending', x17)
                input('computer proceeds to bat')
                t1=0
                while t1<x17:
                    y1=int(input())
                    y2=random.randint(1,10)
                    print(y2)
                    t1+=y2
                    if y1==y2:
                        print('computer is out as its score is:', t1)
                        print('You won the game')
                        sql='update odd_eve set result="won"'
                        cursor.execute(sql)
                        conn.commit()
                        break
                    elif t1>x17:
                        print('you lost the game')
                        sql='update odd_eve set result="lose"'
                        cursor.execute(sql)
                        conn.commit()
                        print('computer score is:', t1)
                        break
    elif p==1:
        cursor.execute('select frequency from odd_eve')
        fetch_1=cursor.fetchone()[0]
        for i in range(1, fetch_1+1):
            cursor.execute(f'select fours from odd_eve where frequency={i}')
            fetch_2=cursor.fetchone()[0]
            print('no of fours in match', i, 'is', fetch_2)
            conn.commit()
    elif p==2:
        cursor.execute('select frequency from odd_eve')
        fetch_1=cursor.fetchone()[0]
        for i in range(1, fetch_1+1):
            cursor.execute(f'select sixes from odd_eve where frequency={i}')
            fetch_2=cursor.fetchone()[0]
            print('no of sixes in match', i, 'is', fetch_2)
            conn.commit()
    elif p==3:
        cursor.execute('select frequency from odd_eve')
        fetch_1=cursor.fetchone()[0]
        for i in range(1, fetch_1+1):
            cursor.execute(f'select tens from odd_eve where frequency={i}')
            fetch_2=cursor.fetchone()[0]
            print('no of tens in match', i, 'is', fetch_2)
            conn.commit()
    elif p==4:
        cursor.execute(f"select frequency from odd_eve where name='{name}'")
        fetch_1=cursor.fetchone()[0]
        for i in range(1, fetch_1+1):
            cursor.execute(f"select bowls_faced from odd_eve where frequency='{i}'")
            fetch_2=cursor.fetchone()[0]
            print('no of bowls played', fetch_2)
            conn.commit()    
    elif p==5:
        cursor.execute('select frequency from odd_eve')
        fetch_1=cursor.fetchone()[0]
        for i in range(1, fetch_1+1):
            cursor.execute(f"select runs_made from odd_eve where frequency='{i}'")
            fetch_2=cursor.fetchone()[0]
            print('net runs in match', i, 'is', fetch_2)
            conn.commit()
    elif p==6:
        cursor.execute('select name from odd_eve')
        fetch_1=cursor.fetchone()[0]
        cursor.execute('select frequency from odd_eve where runs_made=(select max(runs_made) from odd_eve)')
        fetch_2=cursor.fetchone()[0]
        print('dear', fetch_1, fetch_2, 'is the required data')
        conn.commit()
    elif p==7:
        cursor.execute(f"select count(result) from odd_eve where result='won' and name='{name}'")
        count_1=cursor.fetchone()[0]
        cursor.execute(f"select count(result) from odd_eve where result='lose' and name='{name}'")
        count_2=cursor.fetchone()[0]
        print('number of matches won', count_1, 'number of matches lost', count_2)
        conn.commit()
    elif p==8:
        choose=input('name')
        cursor.execute(f"delete from odd_eve where name='{choose}'")
        print('done')
        conn.commit()
    elif p==9:
        new_name=input('Enter the new name')
        data=(new_name, name)
        sql=("update odd_eve set name=%s where name=%s" )
        cursor.execute(sql, data)
        print('made the change')
        conn.commit()
    elif p==11:
        break
    else:
        print('the choice is not right')

conn.close()
