# final_project method-1
------------Admin--------------------
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




 -----------------------------------------------User--------------------------------------------------------
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


 method-2
   ---------------------------------------------------------------------FINAL PROJECT---------------------------------------------------------------------------------------



admin_keys = {"afreen": "afreen@123"}
inven = {1: {'ItemName': 'Tandoori Chicken', 'FoodID': 1, 'Quantity': '100ml,250ml,4pieces', 'Price': 240, 'Stock': 14, 'Discount': '20%'},
        2: {'ItemName': 'Vegan Burger', 'FoodID': 2, 'Quantity': '1 Piece', 'Price': 320, 'Stock': 14, 'Discount': '40%'},
        3: {'ItemName': 'Truffle Cake', 'FoodID': 3, 'Quantity': '500gm', 'Price': 900, 'Stock': 14, 'Discount': '30%'}}
#nested dict
def add_new_item():
    itemname = input("Enter the Item name: ")
    foodid = int(input("Enter the item id: "))
    quantity = input("Enter the Quantity Value of item: ")
    price = int(input("Enter the price of the item: "))
    stock = int(input("Enter the stock value of item: "))
    dis_count = input("Enter the discount value: ")

    inven[itemid] = {
        "ItemName": itemname,
        "FoodID": foodid,
        "Quantity": quantity,
        "Price": price,
        "Stock": stock,
        "Discount": dis_count
    }
    print("The Item"+itemname+ "is successfully added")
    return inven


def edit_from_item():
    item = int(input("Enter the itemid which you want to edit: "))
    a = input("Enter the item name")
    b = int(input("Enter the price of item"))
    d = int(input("Enter the stock of the item"))
    e = input("Enter the quantity of the item")
    f = input("Enter the discount value: ")
    inven[item]["ItemName"] = a
    inven[item]["Price"] = b
    inven[item]["Stock"] = d
    inven[item]["Quantity"] = e
    inven[item]["Discount"] = f
    print("*****Edited item successfully*****")
    return inven

def show_inven():
    print("*****The list item should as follows:*****")
    for i in inven:
        print(inven[i]["FoodID"],'.',end=" ")
        print(inven[i]["ItemName"],end=" ")
        print('(',inven[i]["Quantity"],')',end=" ")
        print("INR", inven[i]["Price"],)
        print("Discount", inven[i]["Discount"])




def remove_item():
    d = int(input("Enter the Item id which you want to exit"))
    inven.pop(d)
    print("Remove item successfully ")
    return inven
import admin as ad
from user import User

uhh = User(str, str, str, str, str)

inp = int(input("Where You want to login select 1.Admin and 2.User and 3.Exit"))
if inp == 1:
    Username = input("Enter the username of admin: ")
    Password = input("Enter the password of admin: ")
    if aa.admin_keys[Username] == Password:
        print("*****You're successfully logged inn*****")
        admin_crawler = True
        while admin_crawler:
            adm_choice = int(input("Choose the options of admin panel 1.ADD NEW ITEM 2.EDIT ITEM 3.VIEW INVENTORY 4.REMOVE ITEM 5.EXIT"))
            if adm_choice == 1:
                aa.add_new_item()
            elif adm_choice == 2:
                aa.edit_from_item()
            elif adm_choice == 3:
                aa.show_inven()
            elif adm_choice == 4:
                aa.remove_item()
            elif adm_choice == 5:
                print(f"You're Exit to the admin panel{Username}")
                admin_crawler = False
            else:
                print("This is the wrong selection please select valid option")
    else:
        print("These are the wrong credentials! SORRY!!!")
elif inp == 2:
    print("Welcome to the user panel")
    username = input("Enter the username here: ")
    password = input("Enter the password here: ")
    if User.login(username, password):
        print(f"You are logged in successfully {username}")
        user_crawler = True
        while user_crawler:
            usr_choice = int(input(f"{username}, Enter the option 1.Place new order 2.Order history 3.Exit"))
            if usr_choice == 1:
                uhh.place_order()
            elif usr_choice == 2:
                print(f"Here is your order history, {username}")
                print(uhh.order_history)
            elif usr_choice == 3:
                user_crawler = False
                print("You're Successfully looged out")
            else:
                print("You choose the invalid option")
    else:
        print("These are the wrong credentials! SORRY!!!")
else:
    exit()

import admin as ad

#a=User(,,,,)#
#b=User(,,,)
#after a -login_info={"a":'a'}
#after b -login_info={"a":'a','b':'b'}

class User:
    login_info = {"afreen": "afreen@123"}

    def __init__(self, name, phoneno, email, address, password):
        self.name = name
        self.number = phoneno
        self.email = email
        self.address = address
        self.password = password
        User.login_info[self.name] = self.password
        self.profile={"Name":name}
        self.order_history = {}

    @classmethod
    def login(cls, username, password):
        if cls.login_info.get(username) == password:
            print("You're are successfully logged in.....")
            return True
        else:
            print("SORRY! These are the Wrong Credentials")
            return False


    def place_order(self):
        print("What you want to order here in the Inventory")
        print(ad.show_inven())
        user_choice = int(input("If you want to order then select 1.YES 2.NO"))
        if user_choice == 1:
            n=int(input("Enter how many items do you want to Order"))
            x=0
            for i in range(n):

             itemid = int(input("Enter the Item id here: "))
             quan = int(input("Enter the quantity of the item: "))
             x += ad.inven[itemid]["Price"] * quan
            again_ask = input("Are you still want to order this Enter YES or NO")
            if again_ask == "YES":
                print(f'''Your item name is {ad.inven[itemid]["ItemName"]}''')
                print(f'''Price of your Item is {ad.inven[itemid]["Price"]}''')
                print(f"This is your quantity {quan}")
                print(f"It costs you {x}INR in total")
                print("You're all set for this order")
                self.order_history[itemid] = {
                    "Item Name": ad.inven[itemid]["ItemName"],
                    "Price": ad.inven[itemid]["Price"],
                    "Quantity": quan
                }
                final_stock = ad.inven[itemid]["Stock"] - quan
                ad.inven[itemid]["Stock"] = final_stock
                print("You're order is successfully placed")

            elif again_ask == "NO":
                print("This Order is cancelled!! You can look once more")
            else:
                print("Invalid choice")
        elif user_choice == 2:
            print("You select 2 option so we cancelled this")
        else:
            print("Enter the invalid choice")
