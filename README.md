import datetime  
from dateutil.relativedelta import relativedelta
from datetime import timedelta  
def calc(strdate,month_to,month_cost,ann):
    
    
    list1=[]
    list1=strdate.split("/")
    #print(list1)
    newdate=datetime.datetime(int(list1[2]), int(list1[1]), int(list1[0]), 0, 0)
    #print(newdate)
    
    added_date = newdate + relativedelta(months=+month_to)
    #print(added_date)
    myday=added_date.day
    if month_to<12:
        if myday<15:
            new_exp=datetime.datetime(added_date.year,added_date.month,1, 0, 0)
            print(new_exp)
            twodate=newdate+relativedelta(months=+(month_to-1))
            
            two1=twodate-new_exp
            extradays=abs(two1.days)-1
            tot_days=extradays+(30*(month_to-1))
            cost=tot_days*(month_cost/30)
            print(cost)
            
            
        else:
            new_exp=datetime.datetime(added_date.year,added_date.month,15, 0, 0)
            print(new_exp)
            diff=added_date-new_exp
            deducted=diff.days
            days=(month_to*30)-deducted
            cost=days*(month_cost/30)
            print(cost)
        
    else:
        if myday>1 and myday<15:
            other_1_exp=datetime.datetime(added_date.year, added_date.month, 15, 0, 0)
            print(other_1_exp)
        if myday==1:
            other_1_exp=datetime.datetime(added_date.year, added_date.month, 1, 0, 0)
            print(other_1_exp)
        if myday==15:
            other_1_exp=datetime.datetime(added_date.year, added_date.month, 15, 0, 0)
            print(other_1_exp)
        if myday>15:
            new_20=(added_date + timedelta(days=20)) 
            other_1_exp=datetime.datetime(new_20.year, new_20.month, 1, 0, 0)
            print(other_1_exp)
        
        
        diff =other_1_exp-added_date
        extra=diff.days
        total_cost=ann+extra*(ann/365)
        print(total_cost)
calc("19/06/2018",3,1000,8000)
