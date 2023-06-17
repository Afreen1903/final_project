# final_project
------------USER--------------------
import uuid

# Printing random id using uuid1()
print ("The food id is : ",end="")
print (uuid.uuid1())
# This loop will go on until the budget is integer or float
while True:
	try:
		bg = float(input("Enter your budget : "))
		# if budget is integer or float it will be stored
		# temporarily in variable 's'
		s = bg
	except ValueError:
		print("PRINT NUMBER AS A AMOUNT")
		continue
	else:
		break

# dictionary to store product("name"), quantity("quant"),
# price("price"),discount("dis") and stock("stock") with empty list as their values
a ={"name":[], "quant":[], "price":[],"discount":[],"stock":[]}

# converting dictionary to list for further updation
b = list(a.values())

# variable na value of "name" from dictionary 'a'
na = b[0]

# variable qu value of "quant" from dictionary 'a'
qu = b[1]

# variable pr value of "price" from dictionary 'a'
pr = b[2]

# variable dis value of "discount" from dictionary 'a'
ds=b[3]

# variable stk value of "stock" from dictionary 'a'
stk=b[4]

# This loop terminates when user select 2.EXIT option when asked
# in try it will ask user for an option as an integer (1 or 2)
# if correct then proceed else continue asking options
while True:
	try:
		ch = int(input("1.ADD\n2.EXIT\nEnter your choice : "))
	except ValueError:
		print("\nERROR: Choose only digits from the given option")
		continue
	else:
		# check the budget is greater than zero and option selected
		# by user is 1 i.e. to add an item
		if ch == 1 and s>0:	
						# input products name			
			pn = input("Enter product name : ")
			#input stock name
			st=int(input("enter stock of the product"))
			# input quantity of product
			q = input("Enter quantity : ")
			# input price of the product
			p = float(input("Enter price of the product : "))
			# input discount of the product
			d= int(input("Enter discount coupon number of the product : "))
            
			
			if p>s:
				# checks if price is less than budget
				print("\nCAN, T BUT THE PRODUCT")
				continue

			else:
				# checks if product name already in list
				if pn in na:
					# find the index of that product
					ind = na.index(pn)

					# remove quantity from "quant" index of the product
					qu.remove(qu[ind])

					# remove price from "price" index of the product
					pr.remove(pr[ind])
					# remove discount from "discount" index of the product
					ds.remove(ds[ind])
										# remove stock from "stk" index of the product
					stk.remove(stk[ind])
					# insert new value given by user earlier
					qu.insert(ind, q)

					# insert new value given by user earlier
					pr.insert(ind, p)
					
                    					# insert new value given by user earlier
					ds.insert(ind, d)
					
                    					# insert new value given by user earlier
					stk.insert(ind, st)
					


					# subtracting the price from the budget and assign
					# it to 's' sum(pr) is because pr = [100, 200] if
					# budget is 500 then s = bg-sum(pr) = 200
					# after updating for same product at index 0 let
					# pr = [200, 200] so s = 100
					s1=s-d
					s = bg-sum(pr)

					print("\namount left", s)
					print("\n amount after discount is: ",s1)
				else:
					# append value of in "name", "quantity", "price"
					na.append(pn)

					# as na = b[0] it will append all the value in the
					# list eg: "name":["rice"]
					qu.append(q)

					# same for quantity and price
					pr.append(p)
					
                    					# append disount coupon  for quantity and price
					ds.append(d)
					
                    					# append stock for quantity and price
					stk.append(st)

					# after appending new value the sum in price
					# as to be calculated
					s1=s-d
					s = bg-sum(pr)
					

					print("\namount left", s)
					print("\n amount after discount is: ",s1)

		# if budget goes zero print "NO BUDGET"
		elif s1<= 0:
			print("\nNO BUDGET")
			break
		else:
		    break

# will print amount left in variable 's'
print("\nAmount left : Rs.", s1)

# if the amount left equals to any amount in price list
if s1 in pr:
	# then printing the name of the product which can buy
	print("\nAmount left can buy you a", na[pr.index(s1)])

print("\n\n\nORDER LIST name,quantity,price,discount,stock")

# print final order list
for i in range(len(na)):
	inputList=na[i], qu[i], pr[i],ds[i],stk[i]
	print(inputList)
	
    #if to remove any item or quantity in list
	remove=int(input("if you want to eliminate any item press '0' else press '1'"))
	
if remove==0:
    inputList_=list(inputList)

    # # Enter the index at which the list item is to be deleted
    givenIndex = int(input("enter serial index num of list if u want to remove"))

    # # deleting the list item at the given index using the del keyword
    del inputList_[givenIndex]

    # # printing the list after deleting a specified list item
    print("List after deleting specified list item:", inputList_)
else:
	print("you haven't removed any")




 ------------------------------------------------Admin--------------------------------------------------------
name = str(input("Enter Your Name : "))
phone_num = int(input("Enter Your phone number : "))
email = str(input("Enter Your Email : "))
password = str(input("Enter Your Password : "))
confPassword=str(input("Conform Your Password : "))
if(password ==confPassword):
   print("User Accepted!")
else:
   print("User Rejected! Invalid Password Combination")
food=["burger","drinks","meals","icecream"]
prices=[5,1,3,2]
myorderFood=[]
myorderCost=[]
counter=0
total=0
print("Welcome to abc food restaurant")
order=input("can i take your order?")
if order=="no":
   exit()
else:
   print("Thank You")

nextOrder= True
while nextOrder==True:

   foodOrder=input("enter your item")
   if foodOrder=="burger":
      myorderFood.append(food[0])
      myorderCost.append(prices[0])
      counter+=1
      total=total+(prices[0])
   elif foodOrder=="drinks":
      myorderFood.append(food[1])
      myorderCost.append(prices[1])
      counter+=1
      total=total+(prices[1])
   elif foodOrder=="meals":
      myorderFood.append(food[2])
      myorderCost.append(prices[2])
      counter+=1
      total=total+(prices[2])
   elif foodOrder=="icecream":
      myorderFood.append(food[3])
      myorderCost.append(prices[3])
      counter+=1
      total=total+(prices[3])
   else:
      print("not on menu")
   finished=input("Have you finished orderong?(y/n)")
   if finished=="n":
      nextOrder=True
   else:
      nextOrder=False
print(myorderFood)
print(myorderCost)
print(counter)
y=0
print("Here is your order")
print(" ")
print("*******")
while y<counter:
   print("Item: ",(myorderFood[y]))
   print("Cost: $"+str(myorderCost[y]))
   y=y+1
   print("The final cost is $ :"+str(total))
